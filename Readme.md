Inside this repository, you can find some subfolders and some videos.

- training-code: this folder contains the code for training the model on ModelArts. To use this script (trainin.py) it is necessary to specify some parameters, the three splits of the datasets (training_set, validation_set and test_set) used for training, the path to the labels (labels.csv that you can find inside dataset folder) and a configurations file (configurations.json) that contains some specifications for the model that can be changed. The datasets splits are a preprocessed version of the synthetically generated image dataset, obtained through the dataset generator. To use the script, first of all, a buchet has been created in which the training code has been loaded, then, a custom algorithm has been created on ModelArts (training_algorithm), used to start the training-jobs. Instead, the dataset has been placed in a second bucket, called dataset. It is also necessary to specify an output folder, in this case it is the training-output folder for which a bucket with the same name has been set up. The output of a training-job which has been started using this algorithm can be found in this bucket. You can find a the training-video that explain the steps.

- training-video: it shows the steps performed to train a model.

- dataset: in this folder you can find the dataset that was used to start the training-jobs on ModelArts. The dataset splits are uploaded to Google Drive and you can download by following the link inside the folder. Furthermore, you can also find the labels in csv format.

- training-output: as mentioned, the output of a training-job flows into the training-output folder located in an OBS bucket with the same name. In this folder you can find the python script to add to the same folder in the OBS bucket to start the deployment of the model on a real-time server. Also you can find a configs.json file which contains the specifics for the server to start. To carry out this operation, AI applications have been created and used to deploy the real-time server. The deploy-video show the process.

- deploy-video: in this video you can find the steps followed to deploy the model on a real-time server.

- APIGW-python-sdk-2.0.4: inside this folder is a script (main.py) that emulates the gesture recognition behavior of the final application. As indicated in the presentation, Mediapipe (Google) is used for the extraction of hand landmarks, which are processed locally and sent to a real-time server for the recognition of the performed gesture. It is, therefore, necessary to specify some parameters in the code to connect to the server..

- hands-capture: At this stage, this is done by the script inside this folder (file_creation_online.py). In the folder you can also find an example of the landmarks that are captured in the video.

- dataset-generator: an ECS service was used to start a Windows Server 2019 machine. Here the code server-side for generating the synthetic dataset was implemented. The Pose.json files have already been manually uploaded to the machine (this part has not yet been automated). Here a web server has been started which allows access to the generation of the dataset in an elementary way. By accessing the following url, you are directed to a web page. A Start button is available here. Clicked, a process starts on the machine which leads to the generation of the synthetic dataset and its download with a Download button which appears at the end of the generation operations. The operation may take a few minutes. The dataset-generator-video shows what happens on the server. A user will simply see a download button appear. This is the url

     http://119.8.214.248:8080/test/

- dataset-generator-video: This video shows the data generation server in operation. It also shows what is happening on the machine, without a logged in user being able to see it,

- apk: this folder contains an android application that shows the final behavior you want to achieve regarding gesture recognition. In this case, gestures can be performed in front of the main/rear camera, with one, two or both hands at the same time.