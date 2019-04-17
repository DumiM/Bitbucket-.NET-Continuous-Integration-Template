# Bitbucket-.NET-Continuous-Integration-Template
>“Continuous Integration doesn’t get rid of bugs, but it does make them dramatically easier to find and remove.” (Martin Fowler, 2006)


## Aim

The main reason for this implementation was to make CI more accessible to students in their first/second year of their Computer Science course

BitBucket Pipelines does not support “building Windows applications” (https://confluence.atlassian.com/bitbucket/limitations-of-bitbucket-pipelines-827106051.html) nor supports .NET Core “out of the box”. It only supports a limited number of languages, but have support for Docker containers. 

Although none of the default build environments for Docker images in BitBucket included .NET Core, Docker Hub (where public and privates Docker images can be stored) has a public image for .NET Core (https://hub.docker.com/r/microsoft/dotnet/)

## How-to
To enable Pipelines a ‘bitbucket-pipelines.yml’ file must be added to the root directory of the repository. This file is used by the pipeline to manage the build configuration.


<img width="200" alt="pipelines_yml_structure2" src="https://user-images.githubusercontent.com/30994223/56277866-7a5d8680-6148-11e9-9d09-b98141a2d77c.png">

```
shows the typical keyword structure of the .yml file
```


For our purpose, only the image and the pipeline script are needed. The image tag looks for the specified docker image and the script executes the commands to perform the build.




![temp yml](https://user-images.githubusercontent.com/30994223/56277953-a973f800-6148-11e9-8763-9121c93d6ad5.JPG)
```
shows the .yml file template I have written. This can be used by any person wishing to
build .net projects using bitbucket. Simply replace ‘(test_folder)’ with the relative path for the
test folder in your repository.
```


Secondly a ‘global.json’ file must be added to the root directory of your
repository. This JSON file is used by the Pipelines to locate the source folder and
the test folder.

![temp glob](https://user-images.githubusercontent.com/30994223/56278006-c3add600-6148-11e9-9819-2cccb787cca8.JPG)
```
shows the global.json template I have written. This can also be used by anyone by simply
replacing the keywords in the parentheses with their respective values.
```

The next step involves inserting ‘project.json’ files into both the source folder and the test folder:


![temp test](https://user-images.githubusercontent.com/30994223/56278076-ecce6680-6148-11e9-8494-bb4fd4a23685.JPG)
```
shows my sample project.json template for the test folder.
```
![temp source](https://user-images.githubusercontent.com/30994223/56278079-ee982a00-6148-11e9-955b-d0980ddf4c33.JPG)
```
shows my sample project.json template for the source folder.
```

Please note that this is just a sample and not all of the frameworks or dependencies shown in the above code needs to be included, simply
the ones that are being used for your particular project. Notice the keyword ‘xunit’, this denotes the testing framework you’re using (in this case XUnit).

![folder struct](https://user-images.githubusercontent.com/30994223/56278174-23a47c80-6149-11e9-8738-35dbd425b0b3.JPG)
```
Note: The folder structure, file locations and the
file names should match the image shown above
```

### Special Thanks to:
Liam Moat
https://bitbucket.org/liammoat/pipelines-dotnet-demo/
