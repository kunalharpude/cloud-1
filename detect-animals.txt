import boto3

if __name__ == "__main__":
    fileName='manbestfriend.jpg'
    bucket='vbtest01'
    
    client=boto3.client('rekognition')

    response = client.detect_labels(Image={'S3Object':{'Bucket':bucket,'Name':fileName}})

    print('Detected labels for ' + fileName)    
    for label in response['Labels']:
        print (label['Name'] + ' : ' + str(label['Confidence']))