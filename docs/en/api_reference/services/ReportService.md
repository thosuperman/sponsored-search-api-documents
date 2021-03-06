# ReportService
Use this service to get, add, or delete reports.<br>
And it provides the operation to download URL of the reports.

#### WSDL
| environment | url |
|---|---|
| production  | https://ss.yahooapis.jp/services/Vx.x/ReportService?wsdl|
| sandbox  | https://sandbox.ss.yahooapis.jp/services/Vx.x/ReportService?wsdl|

#### Namespace
http://ss.yahooapis.jp/V6

#### Overview
Use this service to get, add, or delete reports.

#### Operation
Explains the operation which will be provided at ReportService.

## get
### Request
Gets the list of report that meets the selector criteria.

| Field | Restrictions | Data Type | Description | 
|---|---|---|---|
| selector | Req | [ReportSelector](../data/ReportSelector.md) | Determines which report to return. | 

##### Request Sample
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://ss.yahooapis.jp/V6">
  <SOAP-ENV:Header>
    <ns1:RequestHeader>
      <ns1:license>xxxxxxxxxxxxxxx</ns1:license>
      <ns1:apiAccountId>xxxxxxxxxxxxxxxxxx</ns1:apiAccountId>
      <ns1:apiAccountPassword>passwd</ns1:apiAccountPassword>
    </ns1:RequestHeader>
  </SOAP-ENV:Header>
  <SOAP-ENV:Body>
    <ns1:get>
      <ns1:selector>
        <ns1:accountId>100000000</ns1:accountId>
        <ns1:reportIds>100000003</ns1:reportIds>
        <ns1:reportIds>100000007</ns1:reportIds>
        <ns1:reportIds>100000005</ns1:reportIds>
        <ns1:reportJobIds>100000003</ns1:reportJobIds>
        <ns1:reportJobIds>100000007</ns1:reportJobIds>
        <ns1:reportJobIds>100000005</ns1:reportJobIds>
        <ns1:reportTypes>AD_CUSTOMIZERS</ns1:reportTypes>
        <ns1:reportTypes>TARGET_LIST</ns1:reportTypes>
        <ns1:reportTypes>LANDING_PAGE_URL</ns1:reportTypes>
        <ns1:reportJobStatuses>WAIT</ns1:reportJobStatuses>
        <ns1:reportJobStatuses>COMPLETED</ns1:reportJobStatuses>
        <ns1:reportJobStatuses>IN_PROGRESS</ns1:reportJobStatuses>
        <ns1:reportJobStatuses>FAILED</ns1:reportJobStatuses>
        <ns1:paging>
          <ns1:startIndex>1</ns1:startIndex>
          <ns1:numberResults>10</ns1:numberResults>
        </ns1:paging>
      </ns1:selector>
    </ns1:get>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response
Response Fields

| Parameter | Data Type | Description | 
|---|---|---|
| rval | [ReportPage](../data/ReportPage.md) | A list of report where each entry in the list is the result of applying the operation in the input list with the same index. | 

##### Response Sample
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://ss.yahooapis.jp/V6">
  <SOAP-ENV:Header>
    <ns1:ResponseHeader>
      <ns1:service>ReportService</ns1:service>
      <ns1:remainingQuota>100</ns1:remainingQuota>
      <ns1:quotaUsedForThisRequest>10</ns1:quotaUsedForThisRequest>
      <ns1:timeTakenMillis>0.0173</ns1:timeTakenMillis>
    </ns1:ResponseHeader>
  </SOAP-ENV:Header>
  <SOAP-ENV:Body>
    <ns1:getResponse>
      <ns1:rval>
        <ns1:totalNumEntries>4</ns1:totalNumEntries>
        <ns1:Page.Type>ReportPage</ns1:Page.Type>
        <ns1:values>
          <ns1:operationSucceeded>true</ns1:operationSucceeded>
          <ns1:reportRecord>
            <ns1:accountId>1000000001</ns1:accountId>
            <ns1:reportId>2000000001</ns1:reportId>
            <ns1:reportJobId>3000000001</ns1:reportJobId>
            <ns1:reportJobStatus>COMPLETED</ns1:reportJobStatus>
            <ns1:requestTime>2015/11/30 22:22:30</ns1:requestTime>
            <ns1:completeTime>2015/11/30 23:22:30</ns1:completeTime>
            <ns1:reportDownloadURL>https://ss.yahooapis.jp/report/V6.0/download/3CRAGObSahcIylBoDZS5ftx7qS4VM5jSHqs77QZqmpBFnJFP2jvKe3Dy72UEX3InsUoShWXa3YcX3AmbtqxGco6B</ns1:reportDownloadURL>
          </ns1:reportRecord>
        </ns1:values>
        <ns1:values>
          <ns1:operationSucceeded>true</ns1:operationSucceeded>
          <ns1:reportRecord>
            <ns1:accountId>1000000001</ns1:accountId>
            <ns1:reportId>2000000002</ns1:reportId>
            <ns1:reportJobId>3000000002</ns1:reportJobId>
            <ns1:reportJobStatus>FAILED</ns1:reportJobStatus>
            <ns1:reportJobErrorDetail>INTERNAL_ERROR</ns1:reportJobErrorDetail>
            <ns1:requestTime>2015/11/30 22:22:30</ns1:requestTime>
          </ns1:reportRecord>
        </ns1:values>
        <ns1:values>
          <ns1:operationSucceeded>true</ns1:operationSucceeded>
          <ns1:reportRecord>
            <ns1:accountId>1000000001</ns1:accountId>
            <ns1:reportId>2000000003</ns1:reportId>
            <ns1:reportJobId>3000000003</ns1:reportJobId>
            <ns1:reportJobStatus>IN_PROGRESS</ns1:reportJobStatus>
            <ns1:requestTime>2015/11/30 22:22:30</ns1:requestTime>
          </ns1:reportRecord>
        </ns1:values>
        <ns1:values>
          <ns1:operationSucceeded>true</ns1:operationSucceeded>
          <ns1:reportRecord>
            <ns1:accountId>1000000001</ns1:accountId>
            <ns1:reportId>2000000004</ns1:reportId>
            <ns1:reportJobId>3000000004</ns1:reportJobId>
            <ns1:reportJobStatus>WAIT</ns1:reportJobStatus>
            <ns1:requestTime>2015/11/30 22:22:30</ns1:requestTime>
          </ns1:reportRecord>
        </ns1:values>
      </ns1:rval>
    </ns1:getResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## mutate (ADD)

### Request
Adds report.

| Field | Restrictions | Data Type | Description | 
|---|---|---|---|
| operations | Req | [ReportOperation](../data/ReportOperation.md) | A list of unique operations. | 

##### Request Sample
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://ss.yahooapis.jp/V6">
  <SOAP-ENV:Header>
    <ns1:RequestHeader>
      <ns1:license>xxxxxxxxxxxxxxx</ns1:license>
      <ns1:apiAccountId>xxxxxxxxxxxxxxxxxx</ns1:apiAccountId>
      <ns1:apiAccountPassword>passwd</ns1:apiAccountPassword>
      <ns1:accountId>100000001</ns1:accountId>
    </ns1:RequestHeader>
  </SOAP-ENV:Header>
  <SOAP-ENV:Body>
    <ns1:mutate>
      <ns1:operations>
        <ns1:operator>ADD</ns1:operator>
        <ns1:accountId>1000000001</ns1:accountId>
        <ns1:operand>
          <ns1:reportId>10000000001</ns1:reportId>
        </ns1:operand>
        <ns1:operand>
          <ns1:reportId>10000000002</ns1:reportId>
        </ns1:operand>
      </ns1:operations>
    </ns1:mutate>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response
Response Fields

| Field | Data Type | Description | 
|---|---|---|
| rval | [ReportReturnValue](../data/ReportReturnValue.md) | The list of added reports. | 

##### Response Sample
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://ss.yahooapis.jp/V6">
  <SOAP-ENV:Header>
    <ns1:ResponseHeader>
      <ns1:service>ReportService</ns1:service>
      <ns1:remainingQuota>100</ns1:remainingQuota>
      <ns1:quotaUsedForThisRequest>10</ns1:quotaUsedForThisRequest>
      <ns1:timeTakenMillis>0.0173</ns1:timeTakenMillis>
    </ns1:ResponseHeader>
  </SOAP-ENV:Header>
  <SOAP-ENV:Body>
    <ns1:mutateResponse>
      <ns1:rval>
        <ns1:ListReturnValue.Type>ReportReturnValue</ns1:ListReturnValue.Type>
        <ns1:Operation.Type>ADD</ns1:Operation.Type>
        <ns1:values>
          <ns1:operationSucceeded>true</ns1:operationSucceeded>
          <ns1:reportRecord>
            <ns1:accountId>10000000001</ns1:accountId>
            <ns1:reportId>10000000001</ns1:reportId>
            <ns1:reportJobId>200000001</ns1:reportJobId>
            <ns1:reportJobStatus>WAIT</ns1:reportJobStatus>
            <ns1:requestTime>2011/11/30 23:22:30</ns1:requestTime>
          </ns1:reportRecord>
        </ns1:values>
      </ns1:rval>
    </ns1:mutateResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## mutate (REMOVE)
### Request
Deletes reports.

| Field | Restrictions | Data Type | Description | 
|---|---|---|---|
| operations | Req | [ReportOperation](../data/ReportOperation.md) | A list of unique operations. | 

##### Request Sample
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://ss.yahooapis.jp/V6">
  <SOAP-ENV:Header>
    <ns1:RequestHeader>
      <ns1:license>xxxxxxxxxxxxxxx</ns1:license>
      <ns1:apiAccountId>xxxxxxxxxxxxxxxxxx</ns1:apiAccountId>
      <ns1:apiAccountPassword>passwd</ns1:apiAccountPassword>
      <ns1:accountId>100000001</ns1:accountId>
    </ns1:RequestHeader>
  </SOAP-ENV:Header>
  <SOAP-ENV:Body>
    <ns1:mutate>
      <ns1:operations>
        <ns1:operator>REMOVE</ns1:operator>
        <ns1:accountId>1000000001</ns1:accountId>
        <ns1:operand>
          <ns1:reportJobId>10000000001</ns1:reportJobId>
        </ns1:operand>
        <ns1:operand>
          <ns1:reportJobId>10000000002</ns1:reportJobId>
        </ns1:operand>
      </ns1:operations>
    </ns1:mutate>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response
Response Fields

| Field | Data Type | Description | 
|---|---|---|
| rval | [ReportReturnValue](../data/ReportReturnValue.md) | The list of removed reports. |

##### Response Sample
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://ss.yahooapis.jp/V6">
  <SOAP-ENV:Header>
    <ns1:ResponseHeader>
      <ns1:service>ReportService</ns1:service>
      <ns1:remainingQuota>100</ns1:remainingQuota>
      <ns1:quotaUsedForThisRequest>10</ns1:quotaUsedForThisRequest>
      <ns1:timeTakenMillis>0.0173</ns1:timeTakenMillis>
    </ns1:ResponseHeader>
  </SOAP-ENV:Header>
  <SOAP-ENV:Body>
    <ns1:mutateResponse>
      <ns1:rval>
        <ns1:ListReturnValue.Type>ReportReturnValue</ns1:ListReturnValue.Type>
        <ns1:Operation.Type>REMOVE</ns1:Operation.Type>
        <ns1:values>
          <ns1:operationSucceeded>true</ns1:operationSucceeded>
          <ns1:reportRecord>
            <ns1:reportJobId>200000001</ns1:reportJobId>
          </ns1:reportRecord>
        </ns1:values>
        <ns1:values>
          <ns1:operationSucceeded>true</ns1:operationSucceeded>
          <ns1:reportRecord>
            <ns1:reportJobId>200000002</ns1:reportJobId>
          </ns1:reportRecord>
        </ns1:values>
      </ns1:rval>
    </ns1:mutateResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

<a rel="license" href="http://creativecommons.org/licenses/by-nd/2.1/jp/"><img alt="クリエイティブ・コモンズ・ライセンス" style="border-width:0" src="https://i.creativecommons.org/l/by-nd/2.1/jp/88x31.png" /></a><br />この 作品 は <a rel="license" href="http://creativecommons.org/licenses/by-nd/2.1/jp/">クリエイティブ・コモンズ 表示 - 改変禁止 2.1 日本 ライセンスの下に提供されています。</a>
