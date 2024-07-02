
# CMS Ebba Type Plate API v1.0.0

## 1 Specification 

### 1.1 Communication Protocol

HTTPS

### 1.2 Request Method

POST
GET

### 1.3 Character Encoding
UTF-8

### 1.4 Format Description
Element appears in a requirement description：

Characteristic				|Description
:----:			|:---
R				|Required
O				|Optional
C				|Conditiona

### 1.5 Specification Description 

1. Document specifications are only described for print request data;

2. The content of the request packet in the document specification is the plaintext content of the RequestData value in the HTTPS request;

3. Document specifications are divided into request packets and response packets. The initiator describes the request packet, and the receiver responds to the response packet。



#### 1.6.1 Parameter description
**RequestData：** Each request data using json format.  


#### 1.6.2 Request Data description

Using Json format，Including Header（Public Parameter）、Body（Private Parameter）：

Name		|Description											|Comments
:--		|:--											|:--
Public Parameter	|Each API include public parameter，using JSON format put in Header|
Private Parameter	|Each API include private parameter，using JSON format put in Body and Query Parameter	|



#### 1.6.3 Request Header
Demo：

```
{
    "header":{
        "Content-type":"application/json",
        "Timestamp":"1234567",
        ...
    }
}

```

#### 1.6.4 Request Body
Demo：

```
{
    "body":{
       ...
    }
}

```

#### 1.6.5 Request Query
Demo：

```
/path?popId=2&chassisNo=12...

```


### 1.7 Response Structure
#### 1.7.1 Description
Each response the data is JSON format which include below fields：

Name						|DataType		|Required	|Comments
:----						|:---		|:------	|:---	
Code						|int		|R			|Http code
Msg							|string		|R			|description of response
Data						|object		|R			|playload
Status                      |bool       |R          |status of response

#### 1.7.2 Response Demo

```
{
    "Code":200,
    "Msg":"Get data successful!",
    "Status":true
    "Data":{
       ...
    }
}
```


## 2. API Defination

### 2.1 PostDataToPrinter
- **API Description：** Post data from LMS to printer
- **Path：** /typeplate/postDataToPrinter
- **Method:** Post

#### 2.1.1 Request Parameter


```
{
    "Header":{
        "Content-type":"application/json",
        "Timestamp":1502870664
    },
    "Body":{
        "ID":"18520322032",
        "Model":"acb000000"
        "VinCode":"",
        "DateOfAssembly":"",
        "ModelOfEngine":"",
        "DisplaceOfEngine":"",
        "MaxNetPowerOfEngine":"",
        "WeightOfKerb":"",
        "MaxTotalMassOfPermission":"",
        "MaxTowingMassOfPermission":"",
        "MaxTechStaticPayloadOnFW":"",
        "IntensityOfLight":"",
        "RotateSpeedOfEngine":"",
    }
}

```


#### 2.1.2 Response

Name						|DataType		|Required	|Comments 
:----						|:---		|:------	|:---	
Code						|int		|R			|Code
Msg							|string		|R			|&nbsp;
Status                      |bool       |R          |Status
Data						|object		|R			|&nbsp;


Demo：

```
{
    "Code":200,
    "Msg":"Post Successful",
    "Status":true,
    "Data":{
        
    }
}
```



### 2.2 Print Validation
- **API Description：** verify whether print successful or not
- **Path：** /typeplate/verifyPrint
- **Method:** Get

#### 2.2.1 Request Parameter
  
{
    "Header":{
        "Content-type":"application/json",
        "Timestamp":1502870664
    },
    "Body":{
       
    }
}


#### 2.2.2 Response

Name						|DataType		|Required	|Comments 
:----						|:---		|:------	|:---	
Code						|int		|R			|Code
Msg							|string		|R			|&nbsp;
Status                      |bool       |R          |Status
Data						|object		|R			|&nbsp;

Demo：

```
{
    "Code":200,
    "Msg":"Post Successful",
    "Status":true,
    "Data":{
        
    }
}
```

### 2.3 Reprint
- **API Description：** Reprint 
- **Path：** /typeplate/reprint
- **Method:** Get

#### 2.3.1 Request Parameter
  
```
/path?popId=2&chassisNo=12...

```


#### 2.2.2 Response

Name						|DataType		|Required	|Comments 
:----						|:---		|:------	|:---	
Code						|int		|R			|Code
Msg							|string		|R			|&nbsp;
Status                      |bool       |R          |Status
Data						|object		|R			|&nbsp;


Demo：

```
{
    "Code":200,
    "Msg":"Post Successful",
    "Status":true,
    "Data":{
        
    }
}
```

## 3 Appendix Http Code

Code	|Description 
:----	|:---
100|	Continue
101|	Switching Protocols
102|	Processing
103|	Early Hints
104-199|	Unassigned
200|	OK
201|	Created
202|	Accepted
203|	Non-Authoritative Information
204|	No Content
205|	Reset Content
206|	Partial Content
207|	Multi-Status
208|	Already Reported
209-225|	Unassigned
226|	IM Used
227-299|	Unassigned
300|	Multiple Choices
301|	Moved Permanently
302|	Found
303|	See Other
304|	Not Modified
305|	Use Proxy
306|	(Unused)
307|	Temporary Redirect
308|	Permanent Redirect
309-399|	Unassigned
400|	Bad Request
401|	Unauthorized
402|	Payment Required
403|	Forbidden
404|	Not Found
405|	Method Not Allowed
406|	Not Acceptable
407|	Proxy Authentication Required
408|	Request Timeout
409|	Conflict
410|	Gone
411|	Length Required
412|	Precondition Failed
413|	Content Too Large
414|	URI Too Long
415|	Unsupported Media Type
416|	Range Not Satisfiable
417|	Expectation Failed
418|	(Unused)
419-420|	Unassigned
421|	Misdirected Request
422|	Unprocessable Content
423|	Locked
424|	Failed Dependency
425|	Too Early
426|	Upgrade Required
427|	Unassigned
428|	Precondition Required
429|	Too Many Requests
430|	Unassigned
431|	Request Header Fields Too Large
432-450|	Unassigned
451|	Unavailable For Legal Reasons
452-499|	Unassigned
500|	Internal Server Error
501|	Not Implemented
502|	Bad Gateway
503|	Service Unavailable
504|	Gateway Timeout
505|	HTTP Version Not Supported
506|	Variant Also Negotiates
507|	Insufficient Storage
508|	Loop Detected
509|	Unassigned
510|	Not Extended (OBSOLETED)
511|	Network Authentication Required
512-599|	Unassigned
