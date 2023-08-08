# rapid-deployment-examples

Here we provide example jupyter notebooks to deploy it as API in Exspanse. You can use them to learn structure.

Please note than if we need to return any value from function in API we must use Flask response. In our examples we use Flask jsonify package.

# Rapid Deployments
Document: Rapid Deployment Guide

## 1. Introduction
The Rapid Deployment process enables the transformation of an ipynb notebook into a Python file, which is subsequently deployed as a Flask API service. This guide outlines the necessary steps and best practices to streamline this process.

## 2. Code Structure Guidelines
While you have the flexibility to structure your Python code as you prefer, it is essential to encapsulate all logic within functions or classes. This practice prevents the execution of unnecessary code. However, you are permitted to have constants or variables outside of functions or classes.

## 3. Importing Libraries
When importing libraries, ensure you also include the "jsonify" library from Flask. Insert the following line at the beginning of your ipynb files where you import other libraries:
`
from flask import jsonify
`

## 4. Creating the Prediction Function
Create your prediction function using a name of your choice and any required arguments. This function must return a JSON response using the Flask library's "jsonify" function. Here's an example:

`
def predict_image(image_path):
    image = preprocess_image(image_path)
    with torch.no_grad():
        model = load_model(model_path)
        output = model(image)
        predicted_class = torch.argmax(output, dim=1).item()
    return jsonify(predicted_class)
`

## 5. Initiating Rapid Deployment
With your script prepared, you can now click the "Rapid Deployment" button in the UI.

## 6. Script Verification
In the subsequent pop-up, carefully inspect whether the script accurately fills your prediction function and its arguments. If you identify any discrepancies, make the necessary corrections.

## 7. Machine Selection
Proceed to the next step, where you'll select the desired machine configuration for deployment.

## 8. Deployment
Click the deploy button, initiating the deployment process. That's it!!! All what's remaining to do - just wait deployment status updates.
​
# Next information only for troubleshooting

### Handling Docker Image Build Errors
In the event of errors during the Docker image building process, consult the deployment logs. These logs will highlight issues such as library version mismatches or other potential problems.

### Provisioning Resources
After the container is successfully built, allocate 1-2 minutes for server resource provisioning and API endpoint assignment.

### Making API Requests
Once resource provisioning is complete, you can commence making API requests from the deployment page.

### Error Handling
In case your Python code contains errors, the HTTP logs tab will display error logs, aiding in troubleshooting.
By adhering to these steps, you can swiftly and effectively transform your ipynb notebook into a fully deployed Flask API service, ready to serve predictions.
