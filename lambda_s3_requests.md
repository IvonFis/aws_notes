
<h2>Acceso de Lambda a S3 bucket</h2>

https://aws.amazon.com/es/premiumsupport/knowledge-center/lambda-execution-role-s3-bucket/

Short description
To give your Lambda function access to an Amazon S3 bucket in the same AWS account, do the following:

1.    Create an AWS Identity and Access Management (IAM) role for the Lambda function that also grants access to the S3 bucket.

2.    Configure the IAM role as the Lambda function's execution role.

3.    Verify that the S3 bucket policy doesn't explicitly deny access to your Lambda function or its execution role.

Important: If your S3 bucket and the function's IAM role are in different accounts, then you must also grant the required permissions on the S3 bucket policy. For more information, see How can I provide cross-account access to objects that are in Amazon S3 buckets?

Lambda execution role: https://docs.aws.amazon.com/lambda/latest/dg/lambda-intro-execution-role.html#permissions-executionrole-console

<h2>Layers</h2>
 
 https://medium.com/swlh/how-to-add-python-pandas-layer-to-aws-lambda-bab5ea7ced4f
 
<h2>Query data from Athena from S3 files from a S3 bucket </h2>

https://towardsdatascience.com/query-data-from-s3-files-using-aws-athena-686a5b28e943

How to setup a table in Athena using a sample data set stored in S3 as a .csv file. But for this, we first need that sample CSV file.

To set up the table columns we introduce the datatype as described in here:

https://docs.aws.amazon.com/athena/latest/ug/data-types.html

  
<h2>Append to S3 file </h2>
  
 https://medium.com/@haldis444/use-lambda-to-append-daily-data-to-csv-file-in-s3-2c2813bc33d0

**TODO** CI/CD pipelines https://towardsdatascience.com/modern-ci-cd-pipeline-git-actions-with-aws-lambda-serverless-python-functions-and-api-gateway-9ef20b3ef64a


<h2> Ejemplo Lambda </h2>

~~~python
import json
import requests
import pandas as pd
import boto3

# call s3 bucket
s3 = boto3.resource('s3')
bucket = s3.Bucket('lambda-test-eon')


def lambda_handler(event, context):
    # Sending a GET request and getting back response as HTTPResponse object.
    URL = 'https://ws01.cenace.gob.mx:8082/SWPEND/SIM/SIN/MDA/ACAPULCO/2019/04/19/2019/04/19/JSON'
    r = requests.get(URL)
    result = r.json()
    
    # Extracting the results from the JSON file from CENACE
    list_results = result['Resultados'] # CENACE's information results
    nodo = list_results[0]['zona_carga']

    # Crearting a dataframe for the new values 
    data = pd.DataFrame(columns = ['node', 'date', 'hour', 'pml', 'pml_ene', 'pml_per', 'pml_cng', 'type'])

    valores_list = list_results[0]['Valores']
    for i in list(range(len(valores_list))):
        data.loc[i] = [nodo, valores_list[i]['fecha'], valores_list[i]['hora'],valores_list[i]['pz'],valores_list[i]['pz_ene'],valores_list[i]['pz_per'],valores_list[i]['pz_cng'], 'MDA']
    print(data)
    
    data.to_csv('/tmp/somedf.csv', index=False)
    
    bucket.upload_file('/tmp/somedf.csv', 'temp.csv')
    return {'message': 'success!!'}
~~~
