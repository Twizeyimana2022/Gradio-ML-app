# Gradio-ML-app
Customer churn is a major challenge for many businesses, especially in the telecommunication industry.
Customer churn is a major challenge for many businesses, especially in the telecommunication industry. In order to retain their customers and reduce churn rate, businesses need to be able to predict which customers are likely to leave. In this article, we will walk you through the process of building a Gradio app for predicting customer churn in the telecommunication industry using a machine learning model.
 1: Install Gradio and Import Necessary Libraries
The first step is to install Gradio and import the necessary libraries. Gradio is a Python library that makes it easy to build and deploy machine learning models as user-friendly interfaces.
To install Gradio, runs the following command in your terminal, Vs code, Google Colab (I used Vs code) or Jupyter Notebook:
!pip install gradio
After installing Gradio, we need to import the following libraries:
Import gradio as gr
Import pandas as Pd
Import numpy as np
import pickle
from sklearn.preprocessing import LabelEncoder, StandardScaler
2: Load the Model and Data
We need to load the machine learning model that we will use for predicting customer churn. We also need to load the data that we will use to build our Gradio app.
To load the model, run the following code:
model = pickle.load(open("/content/drive/MyDrive/model (1).pkl", "rb"))
To load the data, run the following code:
data = pd.read_csv('/content/drive/MyDrive/df_churn.csv')
3: Define Input and Output Interfaces for the Gradio App
We need to define the input and output interfaces for our Gradio app. The input interfaces will allow users to input customer data, while the output interface will display the prediction result.
To define the input interfaces, we will create a function called "create_gradio_inputs" that takes the data as input and returns a list of Gradio components. The function will loop over each column in our data and create a Gradio component based on the data type of the column.
Here's the code for the "create_gradio_inputs" function.
To define the output interface, we will create a Gradio Label component that displays the prediction result:
output_components = [
    gr. Label(label="Churn Prediction"),
]
4: Define the Prediction Function
We need to define a function that takes the user inputs, encodes the categorical features, scales the numerical features, and then makes a prediction using the pre-trained model.
You can find the code to define the prediction function here.
In this function, we first create a list of the categorical features and then loop over each feature to encode it using the encoder object that we loaded earlier. We then create a list of the numerical features, scale them using the scaler object, and add them to the encoded_data dataframe. Finally, we make a prediction using the model object and return the prediction as a string. If the prediction is 0, we return "Not Likely to Churn", and if it's 1, we return "Likely to churn".
5: Launch the Gradio App
Now that we have defined the input and output interfaces as well as the prediction function, we can launch the Gradio app using the following code:
# Launch the Gradio app
iface = gr.Interface(predict_churn, inputs=input_components, outputs=output_components,
                     description="Enter the customer's demographic and service usage information to predict whether they are likely to churn or not.")
iface.launch(inbrowser=True, show_error=True, share=True)
This will launch the Gradio app in a new window or tab in your web browser. The app will display the input components (dropdowns, sliders, etc.) that we defined earlier, and the user can enter values for each feature to get a prediction for whether they are likely to churn or not. The output will be displayed as a label below the input components.
If you follow these steps, you can build a Gradio app for telco customer churn prediction using the code provided above. With this app, you can quickly and easily predict whether a customer is likely to churn based on their demographic and service usage information.
