---
notion-id: 2ad982ca-e761-8030-b7e4-fa06ecc98972
---
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>

int countlines(FILE *fp)
{
    int lines = 0;
    int c = fgetc(fp);        /* read first character */
    while (c != EOF) {        /* loop until no more characters */
        c = fgetc(fp);        /* read next character */
        if (c == '\n') lines++;
    }
    rewind(fp); /*resets */
    return lines;
}

int countcolumns(FILE *fp) {
    char text[128], *x;
    int cols=0;

    fgets(text, sizeof(text), fp);
    text[strcspn(text, "\r\n")] = '\0';

    x = strtok(text, ","); /*id*/
    while(x != NULL) {
        x = strtok(NULL, ",");
        cols++;
    }
    rewind(fp);
    return cols;
}

void writegrades(FILE *fpstdnt,int **arr,int width)
{
    char line[256],*endptr;
    int grade,i,j;
    fgets(line, 256, fpstdnt);
    i=0;
    while (fgets(line, 256, fpstdnt))
    {
        arr[i][0] = strtol(strtok(line, ","),&endptr,10);/*id*/
        strtok(NULL, ",");strtok(NULL, ",");/*lname, fname*/
        if (width != 2) strtok(NULL, ",");/*avg*/ 
        for (j=1;j<width-1;j++)
        {
            grade = strtol(strtok(NULL, ","),&endptr,10);
            arr[i][j] = grade;
        }  
        i++;
    } 
    rewind(fpstdnt);
}

void addgrade(FILE *fpactivity,int **arr,int width, int filelength)
{
    char line[256],*endptr;
    int id,i,j;
    fgets(line, 256, fpactivity);
    i=0;
    while (fgets(line, 256, fpactivity))
    {
        id = strtol(strtok(line, ","),&endptr,10);/*id*/
        for (j=0;j<filelength;j++)
        {
            if (arr[j][0] == id) 
            {
                arr[j][width-1] = strtol(strtok(NULL, ","),&endptr,10);
                /*adds grade to the end of each thing*/
            }
        }  
        i++;
    } 
    rewind(fpactivity);
}

void calcavg(int **arr, float *avgArr, int arrlength, int width)
{
    int i,j;
    float sum;
    for (i=0;i<arrlength;i++)
    {
        sum = 0.0;
        for (j=1;j<width;j++) sum += arr[i][j];
        avgArr[i] = sum/(width-1);/*printf("sum=%0.2f",sum);*/
    }
    
}

void writetofile(FILE *fpin,FILE *fpout,int **arr,float *avgArr,int width)
{
    char line[256],*lname,*fname,*endptr;
    int id,i,j;
    fgets(line, 256, fpin);
    fprintf(fpout,"id,last_name,first_name,average,");
    for (i=1;i<width-1;i++) fprintf(fpout,"grade0%i,",i);
    fprintf(fpout,"grade0%i\n",width-1);
    i = 0;
    while (fgets(line, 256, fpin))
    {
        line[strcspn(line, "\r\n")] = '\0';
        id = strtol(strtok(line, ","),&endptr,10);
        lname = strtok(NULL, ",");
        fname = strtok(NULL, ",");
        fprintf(fpout,"%i,%s,%s,%0.2f,",id,lname,fname,avgArr[i]);
        for (j=1;j<width-1;j++) fprintf(fpout,"%i,",arr[i][j]);
        fprintf(fpout,"%i\n",arr[i][width-1]);
        i++;
    } 
    rewind(fpin);
}

int main(int argc, char** argv) {
    FILE * studentfile,*activityfile,*resultfile;
    int numofrows, colnum, **bigArr,i;
    float *avgArr;
    if (argc != 4)
    {
        fprintf(stderr, "not enough args");
        return 1;
    }
    studentfile = fopen(argv[1],"r");
    activityfile = fopen(argv[2],"r");
    resultfile = fopen(argv[3],"w");
    if (!studentfile || !activityfile || !resultfile) 
    {
        if (studentfile) fclose(studentfile);
        if (activityfile) fclose(activityfile);
        fprintf(stderr, "file wont open");
        return 1;
    }
    
    colnum = countcolumns(studentfile) - 2;
    colnum = colnum < 2 ? 2 : colnum;
    numofrows = countlines(studentfile) - 1;/*
    printf("%i, %i\n",colnum, numofrows);printf("%i\n",countcolumns(studentfile));*/
    bigArr = malloc(numofrows * sizeof(*bigArr));

/* allocate each smaller array */
    for (i = 0; i < numofrows; i++) 
    {
        bigArr[i] = malloc(colnum * sizeof(*bigArr[i]));
    }

    avgArr = malloc(numofrows * sizeof(*avgArr));

    writegrades(studentfile, bigArr, colnum);
    addgrade(activityfile,bigArr,colnum,numofrows);
    calcavg(bigArr,avgArr,numofrows,colnum);
    writetofile(studentfile,resultfile,bigArr,avgArr,colnum);
    /*
    printf("bigArr\n");
    for (i = 0; i < numofrows; i++) 
    {
        for (j=0;j < colnum;j++)
        {
            printf("%d, ",bigArr[i][j]);
        }
        printf("\n");
    }
    printf("avgArr\n");
    for (i=0;i<numofrows;i++) printf("%0.2f\n",avgArr[i]);
*/
    free(bigArr);
    free(avgArr);
    fclose(studentfile);
    fclose(activityfile);
    fclose(resultfile);
    return 0;
}
```

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <math.h>

int countlines(FILE*);
float readlines(FILE*,int,char*);
int main(int argc, char** argv) {
    int students,activities,absent,i;
    float mean,stddev;
    FILE * studentfile,*activityfile;
    char *arr;
    if (argc != 3)
    {
        fprintf(stderr, "not enough args");
        return 1;
    }
    
    if (access(argv[1], R_OK) != 0) {
        fprintf(stderr, "problem opening first file\n");
        return 1;
    }

    if (access(argv[2], R_OK) != 0) {
        fprintf(stderr, "problem opening second file\n");
        return 1;
    }

    /*open files after validation*/
    studentfile = fopen(argv[1],"r");
    activityfile = fopen(argv[2],"r");

    students = countlines(studentfile) - 1;
    activities = countlines(activityfile) - 1;
    absent = students - activities;

    arr = malloc(activities * sizeof(*arr));

    mean = readlines(activityfile,students,arr);
        /*printf("%i",arr[i]);*/
    stddev = 0.0;
    for (i=0;i<activities;i++) stddev += pow(arr[i],2.0);
    stddev = sqrt((stddev/students)-pow(mean,2.0));

    printf("total students = %i\nabsent students = %i\ngrade mean = %0.2f\ngrade sd = %0.2f\n",students,absent,mean,stddev);
    fclose(studentfile);
    fclose(activityfile);
    free(arr);
    return 0;
}

int countlines(FILE *fp)
{
    int lines = 0;
    int c = fgetc(fp);        /* read first character */
    while (c != EOF) {        /* loop until no more characters */
        c = fgetc(fp);        /* read next character */
        if (c == '\n') lines++;
    }
    rewind(fp); /*resets */
    return lines;
}

float readlines(FILE *fp,int stdnum,char *arr)
{
    char line[256],*token;
    int i = 0,sum = 0,num;
    fgets(line, 256, fp);
    while (fgets(line, 256, fp))
    {
        token = strtok(line, ",");  /* first token */
        token = strtok(NULL, ",");  /* second token */
        num = atoi(token);
        arr[i] = num;
        sum += num;
        i++;
        /*printf("token: %i, sum: %i\n", num,sum);*/
    } 
    rewind(fp);
    return (float)sum/(float)stdnum;
}
```