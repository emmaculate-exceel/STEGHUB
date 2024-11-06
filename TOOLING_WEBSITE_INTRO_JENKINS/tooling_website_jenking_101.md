# Tooling websites deployments with continous integration 101

#### continous integration and continous deployment


Jenkins is an open-source automation server used to automate various tasks related to continuous integration (CI) and continuous delivery (CD) in software development. It helps developers automate the process of building, testing, and deploying software applications, making the development process faster, more reliable, and less error-prone.


Typical Jenkins workflows :=

1. Commit: Developers commit code changes to a version control system (e.g., Git).
Build Trigger: Jenkins is configured to automatically detect changes in the repository and trigger a build process.
2. Build Process: Jenkins fetches the latest code, compiles it (if needed), and runs tests to ensure the code works as expected.
3. Feedback: If the build is successful, Jenkins proceeds to the next stage (such as deploying the code). If there are issues, Jenkins notifies the developers.
4. Deployment: Jenkins can automatically deploy the code to various environments (like staging or production) after successful builds and tests.