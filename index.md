---
layout: default
---

*IWanDroid* is an information flow analysis for Android WebViews apps. This tool was developed as a research project by Abhishek Tiwari and Jyoti Prakash at the Chair of Software Engineering 1 of University of Passau. 


# Salient Features of Tool  


# Tool
*IWanDroid* in the executable form is available at: https://doi.org/10.5281/zenodo.8279731. 

#Machine Requirement: 64 GB Ram with eight-core processor (for large-scale apps)

##Content of the artifact:
 The Artifacts folder contains 
 1. Dataset Folder: Contains two sub folders named Benchmarks and large-scale_apps. The Benchmarks folder contains the apps in Table V of the paper. The large-scale_apps folder contains all the large scale apps from Fdroid. The selection criteria is mentioned in the Dataset selection (Section V).
 2. Preprocessing folder contains the tool related to the Preprocessing step of our framework (Section IV-A).
 3. The sdk folder contains the Android.jar file.
 4. The iwanDroid-1.0-jar-with-dependencies.jar Jar file contains the implementation for Section IV-B.
 5. Source Code Folder contains the source code of IWanDroid. The latest source code can be found at: https://github.com/mig40000/Demand-driven-IFC-for-Hybrid-apps
 6. Other folders and scripts are used for setting up the docker and tool. 
 
 ##Getting Started and Setup
 We have setup everything in the docker file. The docker image already contains the benchmark apps. Large apps are present in the Dataset/large-scale_apps/largeapps.tgz. To run them, please copy them to the Docker image. To run IWanDroid, please follow the steps as below:

1. Build the Docker image: "docker build -t iwandroid:1.1 ."
2. Run the docker container: "docker run -it iwandroid:1.1"   
3. The root of the docker container is /iwandroid/tool/. The benchmark apps are placed at /iwandroid/Dataset.
4. To run the tool, please run iwandroid.sh from inside the /iwandroid/tool/ directory. (./iwandroid.sh)
5. iwandroid.sh contains various parameters to start the analysis. The path of the preprocessing Database is /iwandroid/tool/Preprocessing/Database/Intent.sqlite
6. To main content is present in the webview_prime table of the Intent.sqlite database. For content description, please refer to Table I (Preprocessed Java-JavaScript Communication data) in the paper.
7. To view the content: sqlite3 Intent.sqlite --> select * from webview_prime;
8. The overall output per app wise is stored in the /iwandroid/tool/logs/ folder
9. To run the analysis on new apps, edit iwandroid.sh and provide the apk path after the -apks tag 
10. To see the detail arguments, please execute: python3 run.py --help

##Known Problems
Sometime in large apps, IWanDroid may crash due to file handling exception. We observed this mainly with very large apps. The error is because of the total number of open file descriptor (ulimit) exceeds the system limit. Usually adjusting it with ulimit solves the problem. Sometimes, running the app in isolation also solves the problem. 

# Citation
Tiwari, Abhishek, Prakash, Jyoti, & Hammer, Christian. (2023). iWanDroid: Demand-driven Information Flow Analysis of WebView in Android Hybrid Apps (1.0) [Data set]. The 34th IEEE International Symposium on Software Reliability Engineering (ISSRE), Florence. Zenodo. https://doi.org/10.5281/zenodo.8279731
# People

- Abhishek Tiwari
- Jyoti Prakash
- Christian Hammer

&copy; [Abhishek Tiwari](https://sites.google.com/view/dr-abhishek-tiwari/home) and [Jyoti Prakash](https://jpksh90.github.io)
