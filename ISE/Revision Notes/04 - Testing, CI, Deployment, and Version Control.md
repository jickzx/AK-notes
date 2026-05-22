# Testing, CI, Deployment, and Version Control

## Testing Stages

- Unit testing tests individual pieces of code. [L12 p7](<../Lecture Slides/12 - Release and Acceptance Testing.pdf#page=7>) [L12 p8](<../Lecture Slides/12 - Release and Acceptance Testing.pdf#page=8>)
- Integration testing tests combinations of pieces and how classes/components work together. [L12 p7](<../Lecture Slides/12 - Release and Acceptance Testing.pdf#page=7>) [L12 p8](<../Lecture Slides/12 - Release and Acceptance Testing.pdf#page=8>)
- Release testing checks whether the full system is ready to show or release to the client. [L12 p13](<../Lecture Slides/12 - Release and Acceptance Testing.pdf#page=13>) [L14 p7](<../Lecture Slides/14 - Configuration and Deployment.pdf#page=7>)
- Acceptance testing checks whether the client accepts the product and is happy to sign off or pay. [L12 p13](<../Lecture Slides/12 - Release and Acceptance Testing.pdf#page=13>) [L14 p7](<../Lecture Slides/14 - Configuration and Deployment.pdf#page=7>)
- User testing happens with real users after or around release and can begin the evolution phase. [L12 p13](<../Lecture Slides/12 - Release and Acceptance Testing.pdf#page=13>) [L14 p8](<../Lecture Slides/14 - Configuration and Deployment.pdf#page=8>)
- Development testing, release testing, and user testing are broader terms used to group testing phases. [L12 p10](<../Lecture Slides/12 - Release and Acceptance Testing.pdf#page=10>) [L12 p11](<../Lecture Slides/12 - Release and Acceptance Testing.pdf#page=11>)

## Release and Acceptance Testing

- Release testing proves to the team that the product is ready for release. [L14 p7](<../Lecture Slides/14 - Configuration and Deployment.pdf#page=7>)
- Acceptance testing is client acceptance, but acceptance should ideally be gained throughout the process. [L14 p7](<../Lecture Slides/14 - Configuration and Deployment.pdf#page=7>)
- User testing, such as alpha/beta release, carefully exposes the product to real users and can reveal future changes. [L14 p8](<../Lecture Slides/14 - Configuration and Deployment.pdf#page=8>)
- Release testing is based on the full functional and non-functional specification. [L12 p7](<../Lecture Slides/12 - Release and Acceptance Testing.pdf#page=7>)
- Acceptance testing is based on user requirements and client/customer expectations. [L12 p7](<../Lecture Slides/12 - Release and Acceptance Testing.pdf#page=7>)

## CI, Configuration, and Deployment

- Release management prepares periodic releases and updates. [L14 p9](<../Lecture Slides/14 - Configuration and Deployment.pdf#page=9>)
- Release management can include release testing and continuous integration. [L14 p9](<../Lecture Slides/14 - Configuration and Deployment.pdf#page=9>)
- Build/configuration management sets up releases for different platforms and environments. [L14 p9](<../Lecture Slides/14 - Configuration and Deployment.pdf#page=9>)
- Continuous integration supports frequent integration of work, automatic testing, and safer release preparation. [L14 p9](<../Lecture Slides/14 - Configuration and Deployment.pdf#page=9>) [L16 p68](<../Lecture Slides/16 - Agile vs Traditional and Maintenance.pdf#page=68>)
- Configuration management helps produce builds for different platforms or platform versions. [L14 p9](<../Lecture Slides/14 - Configuration and Deployment.pdf#page=9>)

## Git and Version Control

- Git supports teamwork through clone, add, commit, push, pull, status, diff, and version history. [L02 p9](<../Lecture Slides/02 - Git Ready for Teamwork.pdf#page=9>)
- Pull before push matters because someone else may have changed the remote repository since your last pull. [L02 p12](<../Lecture Slides/02 - Git Ready for Teamwork.pdf#page=12>) [L02 p29](<../Lecture Slides/02 - Git Ready for Teamwork.pdf#page=29>)
- Git is designed to protect code by keeping history, helping recover old versions, and preventing accidental overwrites. [L02 p15](<../Lecture Slides/02 - Git Ready for Teamwork.pdf#page=15>) [L02 p21](<../Lecture Slides/02 - Git Ready for Teamwork.pdf#page=21>)
- Tags give friendly names to commits and can identify release versions. [L02 p26](<../Lecture Slides/02 - Git Ready for Teamwork.pdf#page=26>)
- Branches let developers work away from the main code and merge work back later. [L13 p5](<../Lecture Slides/13 - Advanced Version Control.pdf#page=5>) [L13 p10](<../Lecture Slides/13 - Advanced Version Control.pdf#page=10>)
- Feature branches and release branches support team workflows and safer releases. [L13 p6](<../Lecture Slides/13 - Advanced Version Control.pdf#page=6>)
- Stashing stores uncommitted changes temporarily when switching tasks. [L13 p15](<../Lecture Slides/13 - Advanced Version Control.pdf#page=15>)
- `.gitignore` keeps generated/build/local files out of version control. [L02 p33](<../Lecture Slides/02 - Git Ready for Teamwork.pdf#page=33>)

## Exam Angles

- If asked to define CI, say code is integrated frequently and automated tests/builds help keep the product working. [L14 p9](<../Lecture Slides/14 - Configuration and Deployment.pdf#page=9>) [L16 p68](<../Lecture Slides/16 - Agile vs Traditional and Maintenance.pdf#page=68>)
- If asked how CI helps deployment, mention automatic tests, automatic builds, configuration scripts, platform-specific builds, and test deployments. [L14 p9](<../Lecture Slides/14 - Configuration and Deployment.pdf#page=9>)
- If asked about release vs acceptance testing, contrast internal readiness against client acceptance. [L12 p13](<../Lecture Slides/12 - Release and Acceptance Testing.pdf#page=13>) [L14 p7](<../Lecture Slides/14 - Configuration and Deployment.pdf#page=7>)
- If asked why Git matters in software engineering, mention coordination, history, conflict handling, branches, review, and traceability. [L02 p15](<../Lecture Slides/02 - Git Ready for Teamwork.pdf#page=15>) [L02 p29](<../Lecture Slides/02 - Git Ready for Teamwork.pdf#page=29>) [L13 p6](<../Lecture Slides/13 - Advanced Version Control.pdf#page=6>)

