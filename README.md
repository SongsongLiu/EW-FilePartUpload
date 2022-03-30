# EW-FilePartUpload

# Project Name
  
  Uppload file part and combine file store to EKV

# Description


# Test request and response

  1、uplaod any file part without file part order.
  2、when the file part count is completed
  3、check the file content and md5

  Example:
  1、request: https://ewcc28.ewcc.in//filePartUpload?fileName=ewcc28&filePartCount=4&fileMD5=APJEdgeWorkersCodingChallenge&filePartIndex=0&filePartContent=APJ

  response:
  ```
    {
        "fileName": "ewcc28",
        "filePartCount": "4",
        "filePartIndex": "0",
        "partJson": {
            "0": {
                "filePartContent": "APJ"
            }
        },
        "partJsonStr": "{\"0\":{\"filePartContent\":\"APJ\"}}",
        "partCount": 1,
        "errMsg": "",
        "content": "APJ",
        "success": false,
        "fileMD": {}
    }
  ```
  2、request: https://ewcc28.ewcc.in//filePartUpload?fileName=ewcc28&filePartCount=4&fileMD5=APJEdgeWorkersCodingChallenge&filePartIndex=3&filePartContent=Challenge
  response:
  ```
    {
        "fileName": "ewcc28",
        "filePartCount": "4",
        "filePartIndex": "3",
        "partJson": {
            "0": {
                "filePartContent": "APJ"
            },
            "1": {
                "filePartContent": "EdgeWorkers"
            },
            "2": {
                "filePartContent": "Coding"
            },
            "3": {
                "filePartContent": "Challenge"
            }
        },
        "partJsonStr": "{\"0\":{\"filePartContent\":\"APJ\"},\"1\":{\"filePartContent\":\"EdgeWorkers\"},\"2\":{\"filePartContent\":\"Coding\"}}",
        "partCount": 4,
        "errMsg": "",
        "content": "APJEdgeWorkersCodingChallenge",
        "success": true,
        "fileMD": {
            "fileName": "ewcc28",
            "fileMD5": "APJEdgeWorkersCodingChallenge",
            "fileContent": "APJEdgeWorkersCodingChallenge"
        }
    }
  ```

  Request Param:
  Name|Description
  ---|---
  fileName| file name
  filePartCount| the count of filepart 
  fileMD5| this param to check file combine completed 
  filePartIndex| file part index, it to use combine file order
  filePartContent| file part content

  Respine Param:
  Name|Description
  ---|---
  fileName| this is from the request.query, to test get the params 
  filePartCount| this is from the request.query, to test get the params 
  filePartIndex| this is from the request.query, to test get the params 
  partJsonStr | Number of existing data in EKV 
  partJson | EKV data to JSON, use JSON.parse(partJsonStr)
  partCount | Number of existing part data in EKV
  errMsg | Program running error log
  success| Successfully identified the composition file
  fileMD| Metadata of final file
