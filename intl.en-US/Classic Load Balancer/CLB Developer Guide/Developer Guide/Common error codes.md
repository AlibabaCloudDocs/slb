# Common error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|ServiceIsConfiguring|A previous configuration is pending; please try again later.|A previous configuration has not been completed. Please try again later.|
|400|VServerGroupProcessing|A previous configuration of the VServer group is pending; please try again later.|A previous configuration of the VServer group has not been completed. Please try again later.|
|400|OperationBusy|A previous operation is pending.|A previous operation is waiting to be completed. Please try again later.|
|400|LX\_REQUEST\_TOKEN\_CONFLICT|The ClientToken is conflict.|The client token conflicts with another token.|
|400|CommodityCodeNotExists|The Account can't get CommodityCode.|Failed to obtain the CommodityCode. Please try again later.|
|400|PAY.PAY\_ORDER\_FAILED|The Acount failed to pay order.|The account failed to pay the order.|
|400|PAY.INVALID\_CREDIT\_CARD|The Acount Credit card is invalid.|The credit card is invalid.|
|400|PAY.REFUND\_FAILED|The Acount failed to Refund.|Failed to refund the money to the account.|
|400|PAY.WITHHOLDING\_AGREEMENT\_ILLEGAL|The Acount withholding agreement is illegal.|The withholding agreement of the account is invalid.|
|400|PAY.COUPON\_NOT\_EXIST|The Acount coupon doesn't exist.|The specified coupon does not exist.|
|400|PAY.STORED\_CARD\_NOT\_EXIST|The Acount stored card doesn't exist.|The specified stored-value card of the account does not exist.|
|400|PAY.ACCOUNT\_BOOK\_NOT\_EXIST|The Acount Book doesn't exist.|The specified reservation of the account does not exist.|
|400|PAY.TAX\_CALC\_FAILED|The Acount Tax failed to calculate.|Failed to calculate the tax of the account.|
|400|PAY.COUPON\_NOT\_MEET\_CONSUMPTION\_RULE|The Acount coupon doesn't meet consumption rule.|The coupon cannot be used, because it does not meet the rules.|
|400|PAY.USER\_DECLINED|The Acount declined to pay.|The payment is declined by the account.|
|400|PAY.INVALID\_AMOUNT|The Acount amount is invalid.|The payment amount is invalid.|
|400|PAY.AMOUNT\_LIMIT\_EXCEEDED|The Acount amount limit exceeded.|The number of accounts has reached the limit.|
|400|PAY.CURRENCY\_NOT\_SUPPORTED|The Acount Currency doesn't support.|The specified currency is not supported.|
|400|PAY.CURRENCY\_INCONSISTENCY|The Acount Currency is inconsistency.|You must use the required currency.|
|400|PAY.NO\_CREDIT\_CARD|The Acount doesn't have Credit Card.|You must link a credit card to the account.|
|400|PAY.GET\_PAY\_URL\_ERROR|The Acount failed to get Pay Url.|Failed to obtain the URL used for payment.|
|400|PAY.PAYMENT\_PARAMETER\_INVALID|The Acount payment parameters are invalid.|The payment parameters of the account are invalid.|
|400|PAY.QUERY\_QUOTA\_BOOK\_FAILED|The Acount failed to query quota book.|Failed to query the quota of the account.|
|400|PRODUCT.INSTANCE\_RELEASED|The Instance is released.|The specified instance is already released.|
|400|PRODUCT.INSTANCE\_TYPE\_NOT\_EXIST|The Instance type doesn't exist.|The specified instance type does not exist.|
|400|PRODUCT.INSTANCE\_TYPE\_NOT\_SUPPORTED|The Instance type doesn't support.|The specified instance type is not supported.|
|400|PRODUCT.NOT\_AVAILABLE\_IZ|The Instance zone id doesn't support.|The specified zone ID is not supported.|
|400|PRODUCT.INSUFFICIENT\_STOCK|The product stock is insufficient.|The request failed due to the shortage of stocks.|
|400|PURCHASE.NO\_VAILD\_PURCHASE|The purchase is invalid.|The purchase failed.|
|400|PURCHASE.PURCHASE\_QUERY\_FAILED|The purchase failed to query.|Failed to query the purchase.|
|400|ORDER.ORDER\_AMOUNT\_ILLEGAL|The order amount is illegal.|The number of orders is invalid.|
|400|ORDER.NOT\_ENOUGH\_ACTIVITY\_STOCK|The order activity stock is not enough.|The request failed due to the shortage of stocks.|
|400|ORDER.SYS\_CONSTRAINT\_INVALID|The order system constraint is invalid.|The attributes of the product in the order failed to pass the constraint verification.|
|400|ORDER.QUANTITY\_INVALID|The maximum number of SLB instances is exceeded.|The number of SLB instances has reached the limit.|
|400|ORDER.PERIOD\_INVALID|The order period is invalid.|The payment cycle is invalid.|
|400|ORDER.BID\_USER\_ ORDER\_FORBIDDEN|The order of bid user is forbidden.|Bid users are not allowed to place orders.|
|400|ORDER.ACCOUNT\_STATUS\_ILLEGAL|The order account status is illegal.|The status of the account does not permit the order.|
|400|ORDER.QUOTA\_EXCEEDED|The order quota exceeded.|The total number of instances has reached the quota. To increase the quota, open a ticket.|
|400|ORDER.OPEND|The account order is open to buy loadbalancer.|You must activate the SLB service for the account.|
|400|ORDER.NO\_REAL\_NAME\_AUTHENTICATION|The account is not real name authentication.|The account must pass the real-name verification.|
|400|ORDER.ARREARAGE|The account is arrearage.|The balance of your account is insufficient. Please update the status of your account and try again.|
|400|ORDER.INSTANCE\_HAS\_INACTIVE\_CHANGE|The instance has inactive change.|An invalid order of instance specification change exists.|
|400|ORDER.INST\_HAS\_UNSETTLED\_BILLS|The instance has unsettled bills.|The instance has unsettled bills.|
|400|ORDER.INST\_HAS\_UNPAID\_ORDER|The instance has unpaid order.|The instance has unpaid bills.|
|400|PRICE.PRICING\_PLAN\_NOT\_FOUND|The instance pricing plan is not found.|Failed to find the pricing plan of the specified instance.|
|400|PRICE.PRICING\_PLAN\_RESULT\_NOT\_FOUND|The instance pricing plan result is not found.|Failed to find the pricing plan of the specified instance. Please open a ticket.|
|400|PRICE.TAXING\_ERROR|The instance pricing tax is error.|The price tax of the instance is invalid.|
|400|PRICE.INVALID\_INQUIRY\_PARAMETER|The instance pricing inquiry parameter is invalid.|The instance pricing query parameter is invalid.|
|400|PRICE.INQUIRY\_FAILED|The instance pricing inquiry is failed.|Failed to query the pricing of the specified instance.|
|400|COMMODITY.INVALID\_COMPONENT|The instance component is invalid.|The instance component is invalid.|
|400|AUTH.RAM\_AUTH\_FAILED|The ram authentication of sub-user is failed.|The access control authentication of the RAM user failed.|
|400|RISK.RISK\_CONTROL\_REJECTION|The Account is rejected by risk control system.|The account is rejected by the risk control system.|
|400|CreateOrderFailed|The Account failed to create order.|Failed to create the order.|
|400|OrderFailed|The Account failed to create order.|Failed to create the order. Please try again later.|
|400|ARREARAGE|The Account has some ARREARAGE.|The account has overdue bills.|
|400|INSUFFICIENT\_BALANCE|The Acount Balance is insufficient.|The balance of the account is insufficient.|
|400|NO\_REAL\_NAME\_AUTHENTICATION|The Account should be Real Name Authenticated.|The account must pass the real-name verification.|
|400|INVALID\_COMPONENT|This Account can't buy such type loadbalancer.|The account is not allowed to buy the specified type of instance. Please choose a different instance type.|
|400|NOCARD|User Profile doesn't have card.|You must link the account to a bank card first.|
|400|RuleNotSupport|Rule is not support in the tcp type listener.|TCP listeners do not support forwarding rules.|
|400|UserProfileNotComplete|User profile is not completed.|You must provide required user information first.|
|400|InvalidParameter|Invalid parameter in the request.|One or more parameters in the request are invalid.|
|400|URLNotSupport|the URL in the rule is invalid.|The specified URL in the rule is invalid. Please check if the URL is correct.|
|409|ServiceIsStopping|The specified Listener is stopping, please retry later.|The specified listener is being stopped. Please try again later.|
|400|AccountHasArrearage|Account has some arrearage.|The account has overdue bills.|
|404|InvalidRuleId.NotFound|Rule does not exist.|The specified rule does not exist.|
|400|OverQuota|Instance num exceeded Quota.|The number of instances has reached the quota.|
|400|NoNameAuthentication|Account should be Name Authenticated.|The account must pass the real-name verification.|
|400|InvalidOwnerAccount|The input parameter OwnerAccount is invalid.|The specified OwnerAccount is invalid.|
|400|InvalidResourceOwnerAccount|The input parameter ResourceOwnerAccount is invalid.|The specified ResourceOwnerAccount is invalid.|
|400|InvalidOwnerId|The specified OwnerId or OwnerAccount is invalid.|The specified OwnerId or OwnerAccount is invalid.|
|400|InvalidOwnerId|The input parameter OwnerId or OwnerAccount is invalid.|The specified OwnerId or OwnerAccount is invalid. Please check if the value is correct.|
|400|OverQuota|The Total is over the quota.|The total number has reached the quota. Please reduce the number and try again.|
|400|ServiceUnavailable|The vpc subnet is not exist.|The VPC subnet does not exist or no IP address is available in the CIDR block of the VSwitch. Please check if the value is correct.|
|400|RegionNotSupport|The specified region not supported.|The specified region is not supported.|
|400|ListenerNumberOverLimit|The maximum number of listeners is exceeded.|The number of listeners has reached the limit. The number of listeners must be no more than 30.|
|400|KeyFormatError|The specified ServerCertificate is incorrectly formatted.|The format of the ServerCertificate parameter is incorrect.|
|400|InvalidParameter|The Lb Name is Not supported.|The specified parameter is invalid.|
|400|InvalidParameter|The Instance is Not Available.|The specified instance is not available.|
|449|SystemBusy|The system is busy.|The system is busy. Please try again later.|
|400|ActionNotAllowed|The action is not allowed.|The operation is not allowed.|
|400|UserNotAllowed|The user is not allowed, please submit the application.|You are not authorized to perform this operation. Please open a ticket.|
|400|SourceItemsQuotaOverLimit|The maximum number of SourceItems is exceeded.|The number of IP addresses has reached the limit of the SourceItems parameter. The number of IP addresses cannot exceed 300.|
|400|ActionNotAllowed|The load balancer instance does not allow to be upgrade.|The specified SLB instance is not allowed to be upgraded.|
|400|ActionNotAllowed|Locked for any Business Reason.|The SLB instance is locked due to service reasons.|
|400|ActionNotAllowed|Locked for any Operate Reason.|The instance is locked due to specification change. It will be unlocked at 00:00 the next day.|
|400|ActionNotAllowed|Listener AccessControl Status is Incorrect.|The access control function of the listener is disabled.|
|400|InvalidParameter|The Protocol is not Support|The protocol is not supported.|
|400|InvalidParameter|The listen bandwidth is not Support|The specified bandwidth of the listener is invalid.|
|400|ActionNotAllowed|The Intranet LB's InternetChargeType is not allowed change to paybybandwidth.|The specified SLB instance is not allowed to be changed to bandwidth-based billing.|
|403|Forbbiden.SubUser|illegal bid|A problem exists with the account.|
|400|InvalidParameter|The specified resource does not exist.|The specified resource does not exist.|
|409|BackendServer.configuring|A previous configuration of the load balancer is pending; please try again later.|A previous configuration of the SLB instance has not been completed. Please try again later.|
|400|ObtainIpFail|The specified BackendServers is invalid; some of the specified backend servers do not exist or are not running.|The specified BackendServers is invalid. Some of the specified backend servers do not exist or are not running. Please check if the value is correct.|
|503|ServiceUnavailable|The specified region not support VPC.|The specified region does not support VPC.|
|400|InvalidParameter|the special internet EIP donot support the VPC network type.|The specified EIP does not support the VPC network type.|
|400|InvalidParameter|The specified load balancer does not support the network type of the ECS instance.|The SLB instance does not support the ECS instance of the specified network type. Please choose an ECS instance of a different network type.|
|400|InvalidParameter|The specified RegionId does not exist.|The specified RegionId does not exist. Please check if the value is correct.|
|400|InvalidParameter|The specified vpc cloud instance has deleted|The specified VPC has already been deleted.|
|400|InvalidParameter|The specified vpc cloud instance is deleteing.|The specified VPC is being deleted.|
|400|PARAMETER\_FIELD\_ERROR|The specified param is invalid.|The specified parameter is invalid.|
|400|InvalidParameter|The vpc info of LB is empty.|The VPC information of the specified instance is empty. Please check if the VPC is valid.|
|400|InvalidParameter|The vpc Ip is exist.|The specified VPC IP address is in use. Please use another IP address and try again.|
|400|InvalidParameter|The Ip is not Supported.|The specified IP address is not supported.|
|400|InvalidParameter|The RsList is illegal.|The specified parameter is invalid.|
|400|InvalidParameter|The Tunnel id is invalid.|The specified tunnel ID is invalid.|
|400|InvalidParameter|The Rs IP is empty.|Failed to obtain the IP address of the backend server.|
|400|InvalidParameter|The VmName is emtpy.|You must specify the ServerId.|
|400|InvalidParameter|The App id is invalid.|The specified app ID is invalid.|
|400|InvalidParameter|The Vgw ip is empty.|You must specify the Virtual Gateway IP address.|
|400|InvalidParameter|The vm address is not Support.|The IP address of the backend server does not permit this operation. Please change the IP address of the backend server and try again.|
|400|InvalidParameter|The site is not exist.|The specified primary and secondary zones are invalid.|
|400|InvalidParameter|The serviceUnit and eip is not match.|The service unit and EIP do not match.|
|400|InvalidParameter|The vgw ip is not support.|The specified Virtual Gateway IP address does not support this operation.|
|503|ServiceUnavailable|Illegal Service.|The service is unavailable.|
|503|ServiceUnavailable|Vpc Service error.|A VPC service error has occurred. Please check the parameter and try again.|
|503|ServiceUnavailable|System exception.|A system error has occurred. Please try again.|
|500|InternalError|Illegal sign.|The system is busy. Please try again later.|
|500|InternalError|Query ecs info fail.|Failed to query the ECS information.|
|500|InternalError|Illegal timestamp.|The specified timestamp is invalid.|
|500|InternalError|Illegal format.|The format is invalid.|
|500|InternalError|Illegal user.|The user is illegal.|
|500|InternalError|Illegal sign type.|The signature type is invalid.|
|500|InternalError|Illegal aliyun idkp.|The account credentials are invalid.|
|503|ServiceUnavailable|The cloud instance id is invaild.|The specified instance ID is invalid.|
|400|InvalidParameter|The type is invalid.|The specified type is invalid. Please check if the type permits the operation.|
|400|InvalidParameter|The lvsgw vip is same.|The specified gateway IP address is in use.|
|400|InvalidParameter|The resource already exists.|The specified resource already exists.|
|400|InvalidParameter|The resource status is invalid.|The resource status is invalid.|
|400|UnsupportedOperationonfixedprotocalport|The operation is not supported by the protocol of the specified port.|The protocol of the specified port does not support the operation. Please check if the protocol of the port is correct.|
|500|InternalError|The request processing has failed due to backend service exception.|The request failed due to an error of the backend service.|
|400|PrivateKeyEncryption|Key has Encrypted .|Private keys do not need to be encrypted.|
|400|CertificateNotMatchPrivateKey|Certificate and key does not match.|The certificate and key do not match. Please check if the certificate and key are correct.|
|400|InvalidParameter|The specified parameter ServerCertificate format is error.|The format of the ServerCertificate is incorrect. Please modify the format and try again.|
|400|CertificateAndPrivateKeyIsRefered|Certificate and PrivateKey Is Refered.|The specified certificate is being used by the listener.|
|400|InvalidParameter|The specified parameter ServerCertificateId is empty.|The specified ServerCertificateId is null.|
|400|InvalidParameter|The specified parameter ServerCertificateId is not Support.|The specified ServerCertificateId is not supported.|
|400|InvalidParameter|The specified parameter ServerCertificate or Key is empty.|The specified ServerCertificate or Key is null.|
|400|InvalidParameter|The specified parameter key format is error.|The format of the key is incorrect.|
|400|InvalidParameter|The specified port is not valid.|The specified port is invalid.|
|400|InvalidParameter|The specified bandwidth is not valid.|The specified bandwidth is invalid.|
|400|VipNotMatchRspool|The vip protocol is not match with Rspool.|The backend server group does not match the listener. Please check the configurations of the backend server group and listener.|
|400|InvalidParameter|The specified Bandwidth is invalid. It exceeds the maximum bandwidth available to the instance.|The specified bandwidth is invalid. The total bandwidth values of all listeners in the instance has exceeded the maximum bandwidth of the instance.|
|400|InvalidParameter|The specified Bandwidth is invalid.|The specified bandwidth is invalid. Please check if the bandwidth is correct.|
|400|InvalidParameter|The specified SourceItems is invalid.|The specified SourceItems is invalid. Please check if the value is correct.|
|400|VipTooManyListeners|The total number of input listeners exceeds max supported number: 10|Up to 10 listeners can be created for an instance. The number of listeners has exceeded the limit.|
|400|InvalidParameter|The specified protocol is not valid.|The specified protocol is invalid.|
|404|InvalidParameter|The specified VServerGroupId does not exist.|The specified VServerGroupId does not exist. Please check if the value is correct.|
|400|InvalidParameter|Illegal user ID.|The user ID is invalid.|
|400|InvalidParameter|User ID is null|You must specify the user ID.|
|400|InvalidParameter|The specified parameter: lb\_type is not valid.|The specified lb\_type is invalid.|
|400|InvalidParameter|The specified parameter: mode is not valid..|The specified mode is invalid.|
|503|ServiceUnavailable|The specified loadbalancer name has been used.|The specified SLB instance name is being used by another instance.|
|400|TcpNotSupportForHybridLb|Hybrid type loadbalancer doesn't support TCP type listener|Hybrid SLB instances do not support TCP listeners.|
|400|InvalidParameter|The specified BackendServers is invalid.|The specified BackendServers is invalid. Please check if the value is correct.|
|400|InvalidParameter|The specified BackendServers is invalid, as the Port value should be in \[1, 65535\].|The specified BackendServers is invalid. Please make sure that the port number falls into the range of 1 to 65535.|
|400|UnsupportedOperation|The Loadbalancer doesn't support this function.|SLB does not support this function.|
|400|TooManyBackendServers|The total number of input real servers exceeds max supported number: 20|Up to 20 backend servers can be specified in one request. The number of specified backend servers has exceeded the limit.|
|400|InvalidParameter|The specified parameter is not valid.|The specified parameter is invalid. Please check if the value is correct.|
|400|InvalidParameterLength|The specified parameter length is not valid.|The length of the parameter value is invalid.|
|400|InvalidAuthorization|The Request is not authorization.|The request is not authorized.|
|500|InternalInvokeError|The internal invoking has failed due to unknow error.|The request failed to be processed due to unknown errors.|
|400|OssInstanceDataNotFound|The oss instance of the demand is not exist|The specified OSS instance does not exist.|
|400|InvalidAuthorizationStatus|The authorization status is not valid.|The authorization status is invalid.|
|500|InternalInvokeError|The internal invoking has failed.|An internal error has occurred.|
|400|InsufficientCapacity|There is insufficient capacity available for the requested|The number of SLB instances has reached the quota. To increase the quota, open a ticket.|
|400|ProcessingSameRequest|The same request is being processed. Please try later.|A same request is being processed. Please try later.|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist.|The specified RegionId does not exist. Please check if the product is available in the specified region.|
|404|InvalidServerId.NotFound|The specified ServerId does not exist.|The specified ServerId does not exist. Please check if the value is correct.|
|503|InvalidParameter|The request has failed due to a temporary failure of the server.|The request failed due to a server failure.|
|400|InvalidParameter|Specified parameter is not valid.|The specified parameter is invalid.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server now.|The request failed due to a server failure.|
|400|UnsupportedOperation|The specified action is not supported.|The operation is not supported.|
|400|ListenerAlreadyExists|A listener with the specified port already exists|The specified port number is already associated with another listener.|
|404|ListenerNotFound|You have not created a listener for the specified port of the load balancer.|You must create a listener for the specified port of the SLB instance first.|
|404|CheckedListenerNotFound|No health-checked Listener to the specified port of the Load Balancer.|You must configure health checks for the specified SLB instance first.|
|400|IpNotAvailable|The specified network type load balancer load balancer .|The specified network type of the SLB instance is invalid. Please check if the value is correct.|
|400|InvalidWeight.Malformed|A specified weight is not valid.|The specified weight is invalid.|
|500|IncorrectListenerAccessControlStatusStatus|Current listener access control status does not support this operation.|The access control status of the listener does not permit this operation.|
|400|MissingParameter|The combination of some parameters violates the spec.|The request parameters are in conflict.|
|400|UnsupportedParameter|The specified parameter is not unsupported.|One or more parameters are not supported.|
|403|Forbidden|User not authorized to operate on the specified resource.|You are not authorized to operate on this resource. Please apply for RAM permissions and try again.|
|400|TooManyBackendServers|The backend server parameter has too many entries.|The number of specified backend servers in a request has exceeded the limit.|
|403|Forbbiden.SubUser|TUser not authorized to operate on the specified resource as your account is created by another user.|This user is not authorized to operate the resources under the specified account. Please authorize the user first.|
|400|InvalidBackendServers.Inconsistent|All BackendServers on one Specified LoadBalancer have to be in the same vpc or all classic|All backend servers of an SLB instance must belong to the same VPC or classic network.|
|400|InvalidServerId.NotFound|The specified server is not found.|The specified backend server does not exist.|
|400|InvalidIdentity|The request identity was not allowed operated.|The request authentication failed.|
|400|DomainAlreadyExists|Protected DomainName already exists.|The specified domain name already exists.|
|400|DomainNotExisted|Don't delete or update not existed protected DomainName.|The specified domain name does not exist.|
|400|IpListItemFormatError|please check the ip list item format error.|The format of the IP address list is incorrect.|
|400|SecurityNotSupport|security function not support on this listener.|The specified listener does not support the security function.|
|400|DomainExist|rule with same domain and url already exists in specified vip|A rule with the same domain name and URL already exists.|
|400|TooManyRules|the number of rules under specified vip is beyond maximum limit.|The number of rules added for the listener has exceeded the limit.|
|400|RspoolVipExist|there are vips associating with this vServer group.|The specified VServer group is already associated with another listener. Please disassociate the VServer group first.|
|400|RspoolRuleExist|there are rules associating with this vServer group.|The specified VServer group is associated with a forwarding rule. Please disassociate the VServer group from the forwarding rule.|
|400|BackendServersMalformed|the specified parameter BackendServers is unavailable.|The specified BackendServers is invalid.|
|400|RuleListMalformed|the specified parameter RuleList is unavailable.|The specified RuleList is invalid.|
|400|DomainMalformed|the specified domain in RuleList parameter is unavailable.|The format of the specified domain is invalid.|
|400|UrlMalformed|the specified url in RuleList parameter is unavailable.|The specified URL in the RuleList parameter is invalid.|
|400|NetworkConflict|there are network conflicts in specified parameter.|Networks specified in the parameters conflict with each other. Please check if the values are correct.|
|400|VServerGroupEmpty|The specified VServerGroupId is invalid; it does not contain vServers.|The specified VServerGroupId is invalid. Make sure that it contains VServers and try again.|
|400|VpcZoneNotSupportCreate|The specified zone dont not supported .|The specified zone does not support VPC.|
|400|VpcStatusError|the specified vpc status is creating.|The specified VPC is being created.|
|400|TagCreateCountLimit|tags create count limit exceeded.|The number of tags has exceeded the quota.|
|400|TagCountLimit|Tags count limit exceeded.|The number of tags has exceeded the quota.|

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

