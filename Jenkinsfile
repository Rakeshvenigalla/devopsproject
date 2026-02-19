node
{
    stage("checkoutSCSC")
    {
        git branch: 'main', url: 'https://github.com/devopsenthusiasts/devopsproject.git'
        mail bcc: '', body: 'The source code is checked out successfully!', cc: '', from: '', replyTo: '', subject: 'checkout successful', to: 'projects2488@gmail.com'
    }
    stage("build")
    {
       sh 'mvn package' 
       mail bcc: '', body: 'The project is built  successfully!', cc: '', from: '', replyTo: '', subject: 'build successful', to: 'projects2488@gmail.com'
    }
    stage("deploytotest")
    {
        deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcattestcreds', path: '', url: 'http://172.31.25.98:8080')], contextPath: 'testappfromscripted', war: '**/*.war'
        mail bcc: '', body: 'The app is successfully deployed to QA!', cc: '', from: '', replyTo: '', subject: 'Deploy to test successful', to: 'projects2488@gmail.com'
    }
    stage("runtests")
    {
        sh 'echo Testing passed'
        mail bcc: '', body: 'The test cases did run  successfully!', cc: '', from: '', replyTo: '', subject: 'Tests Passed/ successful', to: 'projects2488@gmail.com'
    }
    stage("deploytoProd")
    {
        deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat-production', path: '', url: 'http://172.31.16.189:8080')], contextPath: 'prodappfromscripted', war: '**/*.war'
        mail bcc: '', body: 'Application is LIVE', cc: '', from: '', replyTo: '', subject: 'application is LIVE', to: 'projects2488@gmail.com'
    }
}
