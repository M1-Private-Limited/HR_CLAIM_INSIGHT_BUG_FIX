<h1 align="center">
  <a href='https://github.com/M1-Private-Limited'>
    <!-- Please provide path to your logo here -->
    <img src='https://github.com/ONGQ0019/filedumps/raw/main/download-removebg-preview.png' alt="Logo" width="100" height="100">
  </a>
</h1>

<div align="center">
  Machine Learning Application 
  <br />
  <a href="https://user-images.githubusercontent.com/102540895/205837434-c0a1a9c6-8061-4766-af85-28db9c8201cc.mp4"><strong>Watch intro video »</strong></a>
  <br />
  <a href="https://github.com/M1-Private-Limited/MACHINE_LEARNING_APP/discussions/1">Report a Bug or request for a feature</a>
</div>

<details open="open">
<summary>Table of Contents</summary>

- [About](#about)
  - [Built With](#built-with)
  - [Objective](#Objective)
- [Use case](#use-case)
- [Functions](#functions)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [Security](#security)

</details>

---

## About

> A machine learning application developed by M1 Data Team that allows users to segment data themselves and use our pre-trained model against the segmented dataset for data exploration and analysis.




</details>


### Built With


Streamlit on python, hosted on Azure Web App and compartmentalized in Github.

<details open="open">
<summary>Expand Architecture Diagram</summary>
  <img width="600" alt="cccb" src="https://user-images.githubusercontent.com/102540895/205845331-4fcd6f2f-aa33-4cc4-ac2e-06f0d78f71c4.png">
</details>


### Objective

Make ML-trained models more accesible, interpretable, effective and reproducible to both data scientists and end-users.

<details open="open">
<summary>Expand Objective Diagram</summary>
  <img width="347" alt="vvcdz" src="https://user-images.githubusercontent.com/102540895/205845561-2862b9f1-2b80-4fa9-bbab-4ff9edae8974.PNG">
</details>





## Use case

Use case :one:: Find out the minimum cost, revenue, take-up rate and model accuracy needed to execute a sustainable campaign.

Use case :two:: Use sensitivty analysis to discover the best target segment to use the model on. 

Use case :three:: Find out which are the top differential attributes between 2 datasets (Month over Month or Positive vs Negative Group)

Use case :four:: Forecast sales based on attribute combinations.

Use case :five:: Receive visual explanation of how each feature contributes to the model's predictions.

Use case :six:: Enable data scientists to easily insert new models/datasets.


## Functions

>:m: Data Segmentation

Segments the data based on the user's selected attributes and reruns the model on the segmented groups. It also allows the user to select the number of exports to be made and displays the original number of positives and negatives before the data is segmented.

>:m: Feature Importance

Function calculates and displays the SHAP (SHapley Additive Explanations) feature importance for the trained model. It uses the trained model and the data to calculate the SHAP values and displays a summary plot of the feature importance (how much a feature contributes to the model's ability to predict the outcome). 

>:m: Goal Seek

Used to determine whether the model's performance meets the actual requirements. The user is asked to input relevant data points, such as the number of targets, take up percentage, cost, and revenue, and then the function uses these inputs to calculate whether the model's performance meets the requirements. The function also outputs the required model accuracy and the actual model accuracy, as well as the profit or loss.

>:m: Sensitivity Analysis

Generates a graph based on user inputed attributes- a graph for each value in the list by applying the model to the corresponding segment of the data, and adds the results to the dataframe. Users can see the most profitable/revenue generating segment to be targeted. 

>:m: Profiling

Function automatically performs a number of operations on a given data set, such as calculating basic statistics, identifying missing values, and detecting outliers. It then generates a profiling report that summarizes the key characteristics of the data. It also allows the user to filter the dataframe and download the filtered data. 

>:m: Datadrift

Function creates an interactive bar plot to show the data drift for a selected attribute. Data drift is a phenomenon that occurs when the distribution of a data set changes over time. Statistical tests are performed on each categorical attribute.

>:m: ARIMA Forecasting

ARIMA (short for Autoregressive Integrated Moving Average) used to predict Handset sales. Users can interact with the given attributes and segment the dataset to view the predicted sales for the segmeented dataset.

>:m: Forecast Dashboard

Visualization dashboard for forecasted handset sales of different brand/time period.
Similar to the tableau dashboard in: https://tabl02/views/SALESFORECAST_16669185287570/ForecastDashboard?:showAppBanner=false&:display_count=n&:showVizHome=n&:origin=viz_share_link

## Roadmap

For upcoming 2023:

- Include more models and maybe a recommendation system
- Resolve unresolved bugs
- Bring in more contributors 


## Contributing

To contribute your model and dataset to this project. Please follow the codes below:

Under mainpage(), add in these lines of code
```python
    if st.button('Preload YOUR_MODEL_NAME'):
        with st_lottie_spinner(lottie_load,height =200, width = 200):
        blob_model = BlobClient(account_url="https://zpdsnfsa07.blob.core.windows.net",
                                container_name="newstack",
                                blob_name="YOUR FILEPATH",
                                credential="YOUR CREDENTIALS")
        data_model = blob_model.download_blob()
        with open("MODEL_NAME.sav", "wb") as f_model:
            data_model.readinto(f_model)
            st.session_state.model = pd.read_pickle(r'MODEL_NAME.sav')
            model = st.session_state.model

        blob = BlobClient(account_url="https://zpdsnfsa07.blob.core.windows.net",
                          container_name="newstack",
                          blob_name="YOUR FILEPATH",
                          credential="YOUR CREDENTIALS")
        data = blob.download_blob()
        with open("FILE_NAME.csv", "wb") as f:
            st.experimental_memo.clear()
            data.readinto(f)
            st.session_state.dataframe = pd.read_csv("FILE_NAME.csv")
            time.sleep(1)
        st.success('Data ingested sucessfully!')
```




## Security

Security Issues:

- Github repo is never to be set public, only private.
- Dataset to be stored in azure blob storage only.
- Private endpoints must be set up to only allow Users connected to M1 network to use this application. 
- Downloaded Dataset is not to be used for campaigns directly.
- GB Limit Per user to prevent spams.


