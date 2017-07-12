# Source 2 Image Example

Sample Java Web Application for use in OpenShift

#### 1 - create new project
`oc new-project demo-s2i \
--display-name="Demonstração Básica do S2I" \
--description="Demonstração básica do build strategy S2I, usando o EAP 7"`

#### 1 - create the new Java web application
`$ oc new-app --name=myapp jboss-eap64-openshift~https://github.com/leomachadorocha/os-sample-java-web.git`
```
--> Creating resources with label app=myapp ...
    imagestream "myapp" created
    buildconfig "myapp" created
    deploymentconfig "myapp" created
    service "myapp" created
--> Success
    Build scheduled, use 'oc logs -f bc/myapp' to track its progress.
    Run 'oc status' to view your app.
```
#### 2 - expose the service
`$ oc expose svc myapp`
```
route "myapp" exposed
```

#### 3 - get information about the deployment
`$ oc status`

#### 4 - make changes to the src/main/webapp/index.jsp file

#### 5 - start a new build
`$ oc start-build myapp`

#### 6 - see the changes applied

fonte: https://blog.openshift.com/getting-started-with-jboss-enterprise-application-platform/
