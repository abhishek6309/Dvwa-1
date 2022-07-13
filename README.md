# Dvwa-sast

# 1 ) Performing Static Application Security Testing Using SonarQube on DVWA ( Damn Vulnerable Web Application):

1 Download DVWA source code from https://github.com/digininja/DVWA

2 Open SonarQube Click on create project and add an project name like " DVWA Source code review "

3 Go to With the configuration best suited for you in this we will go manually with GitHub Actions

4 we have to Create GitHub Secrets in our repository containing DVWA source code

5 Create a " sonar-project.properties " file in your repository and paste the content mentioned in below :
sonar.projectKey=DVWA-Source-code-review-

6 Create or update your .github/workflows/build.ymland paste the content mentioned below::

" name: Build on:
 push:
   branches:
     - master # or the name of your main branch
jobs
 build:
   name: Build
   runs-on: ubuntu-latest
   steps:
     - uses: actions/checkout@v2
       with:
         fetch-depth: 0
     - uses: sonarsource/sonarqube-scan-action@master
       env:
         SONAR_TOKEN: $Template:Secrets.SONAR TOKEN
         SONAR_HOST_URL: $Template:Secrets.SONAR HOST URL
     # If you wish to fail your job when the Quality Gate is red, uncomment the
     # following lines. This would typically be used to fail a deployment.
     # - uses: sonarsource/sonarqube-quality-gate-action@master
     #   timeout-minutes: 5
     #   env:
     #     SONAR_TOKEN: $Template:Secrets.SONAR TOKEN
"

7 Commit and push your code to start the analysis. Each new push you make on your main branch will trigger a new analysis in SonarQube

# Observations:

1 SonarQube will give you detailed analysis report within 5 minutes which will help you to improve your code quality

2 The results of analysis will be as following:

-58 Bugs
-0 Vulnerabilities
-59 Security Hotspots
-404n Code Smells
-10.6% Duplications

You can then see the details of bugs , code smells , etc. found by clicking on then
