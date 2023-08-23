# Result Validation

This section is to validate the functionality of the continuous integration and continuous deployment pipeline in order to deploy a web application to the SIT and Production cluster. It involves deploying the web application to the SIT cluster before the version of the application can be released to the production environment. The version of the web application to be released to both environments is in red color background. Throughout different testing, we will use different color-coded backgrounds to represent different versions of the application to be released to the SIT and Production environment.

###	Validation of System Integration Testing (SIT) Environment
1. Look for the index.php file under the CodeArts-Repo-Name/index.php directory, within the <style> tag, uncomment the scripts for the background parameter where the value represents the red color as in the below screenshots.

    ![figure8.1.0](./images/8.1.0.png)

<p align="center"> Figure 8.1.0: Modify the index.php file </p>

2. Within the <style> tag, uncomment the scripts for the background parameter for all the sections as mentioned below:
* .highlight-box {}
* footer {}
* .shaded-section h2 {}

3. Once modify the code, commit changes to the CodeArts Repo using the below command to trigger the SIT pipeline by following the instructions in the below screenshot.

```$ git commit -am “deploy history red version”```

```$ git push```

![figure8.1.1](./images/8.1.1.png)

<p align="center"> Figure 8.1.1: Commit changes to the CodeArts Repo </p>

4. Navigate to the CodeArts Pipeline management console, and verify the SIT pipeline was triggered upon source code commit.

    ![figure8.1.2](./images/8.1.2.png)

<p align="center"> Figure 8.1.2: Verify the SIT pipeline was triggered upon code commit </p>
    
![figure8.1.3](./images/8.1.3.png)

<p align="center"> Figure 8.1.3: Verify the SIT pipeline had run successfully </p>

5. Once the pipeline had run successfully, configure a load balancer in the SIT cluster in order to access the web application using the EIP bound. Follow the instructions in the below screenshot to configure the ELB.

    ![figure8.1.4](./images/8.1.4.png)

<p align="center"> Figure 8.1.4: Verify the SIT pipeline had run successfully </p>

![figure8.1.5](./images/8.1.5.png)

<p align="center"> Figure 8.1.5: Verify the SIT pipeline had run successfully </p>

6. Obtain the EIP address of the load balancer and paste it into any web browser to access the web application. If you see a similar result as in Figure 2.1.7, it indicates that you had completed the configuration and validation on the CI pipeline.

    ![figure8.1.6](./images/8.1.6.png)

<p align="center"> Figure 8.1.6: Obtain the EIP address of the load balancer </p>

![figure8.1.7](./images/8.1.7.png)

<p align="center"> Figure 8.1.7: Verify the web application </p>

7. In the meantime, you can also check the container image that had built using the SIT pipeline. Navigate to the Software Repository Warehouse (SWR) management console, and verify the container image built.

    ![figure8.1.8](./images/8.1.8.png)

<p align="center"> Figure 8.1.8: Container image built and pushed to SWR </p>