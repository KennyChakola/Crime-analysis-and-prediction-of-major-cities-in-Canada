# Crime Analysis and Prediction of Major Cities in Canada

The objective is to analyze the crime data of 7 Canadian cities over the past and predict  the  estimated  crime rates  for  the  following year. 

Below steps are required to make this code work:

*  Create a keyspace and the relevant tables in Cassandra DB - You would need to access the cluster and open cqlsh to perform the setups.Setup commands are present in folder 'Cassandra Keyspace and Tablesetups'

Note - Codes and Data for below steps are present in folder 'data_loaded_code'
*  Post creating the tables please run the below codes to insert values into configuration tables
        # Run the below code using crime_types.csv:
        `spark-submit --packages datastax:spark-cassandra-connector:2.4.0-s_2.11 crimetypes_loader.py`
        
        2.Run the commands in cqlsh to perform inserts into crime_code table. Commands are present in crime_code_-_table_inserts.txt
            

*  Run the codes to perform ETL for the following cities . Commands are provided as below
        
    To load Vancouver Data from OpenDataPortal
    `spark-submit --packages datastax:spark-cassandra-connector:2.4.0-s_2.11 van_load.py`
        
    To load Calgary Data from OpenDataPortal
    `spark-submit --packages datastax:spark-cassandra-connector:2.4.0-s_2.11 cal_load.py`
        
    To load Toronto Data from OpenDataPortal
    `spark-submit --packages datastax:spark-cassandra-connector:2.4.0-s_2.11 toronto_load.py`  
        
    To load Ottawa Data from OpenDataPortal
    `spark-submit --packages datastax:spark-cassandra-connector:2.4.0-s_2.11 ottawa_load.py`
        
    To load Victoria Data from OpenDataPortal
    `spark-submit --packages datastax:spark-cassandra-connector:2.4.0-s_2.11 victoria_load.py`
        
    To load Lethbridge Data from OpenDataPortal
    `spark-submit --packages datastax:spark-cassandra-connector:2.4.0-s_2.11 lethbridge_load.py` 
        
    To load Edmonton Data from OpenDataPortal
    `spark-submit --packages datastax:spark-cassandra-connector:2.4.0-s_2.11 edmonton_load.py`

Note - Codes and Data for below steps are present in folder 'Visualization'
*  Now that our data is loaded , please run the following code to perform descriptive analytics of the loaded data
    `spark-submit --packages datastax:spark-cassandra-connector:2.4.0-s_2.11 crimetypcnt.py`

Note - Codes and Data for below steps are present in folder 'Crime_Rate_Predictor'
* We also have developed a prediction model that can predict the crime rates based on neighbourhood radius of 1.5km. To train the model, please run the below code
        
    `spark-submit --packages datastax:spark-cassandra-connector:2.4.0-s_2.11 training_data_loader.py`

    `spark-submit --packages datastax:spark-cassandra-connector:2.4.0-s_2.11 crime_predictor.py`

Note - Codes and Data for below steps are present in folder 'Web Deployment'
* To render the descriptive analytics(developed in Tableau) and the prediction model, please run the below code . Ensure all the htmls present in the master directory are present along with the code while running

    `spark-submit main.py`
