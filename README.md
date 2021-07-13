-----------------------------------------------------ODC team to Access to Azure Environments------------------------------------------------------------------------------
I.	Azure Dev & Test
1)	Step 1: RDS to 172.16.3.89 with domain account dicentral\your account. Request Thanh Thai add your account to RDS group if your domain account was not existing in RDS group
2)	Step 2: From 172.16.3.89 RDS to VM on Azure Dev & Test with accounts:
a)	dicservices\odcrouser1 (pass: m923DxfvVr)
b)	dicservices\odcrouser2 (pass: D!c@#$%^&*19)

II.	Azure Staging & PROD  (2hours/session)
1)	Step 1: Request IT team to open access to GW 172.16.1.248
2)	Step 2: RDS to 172.16.1.248 with accounts:
a)	dicentral\odcrouser1 (pass: m923DxfvVr)
b)	dicentral \odcrouser2 (pass: D!c@#$%^&*19)

3)	Step 3: From 172.16.1.248 RDS to VM on Azure Dev & Test with accounts:
i)	CACIP: (10.5.x.y)
(1)	User1: cadicservices\odcrouser1 (pass: m923DxfvVr12)
(2)	User2: cadicservices\odcrouser2 (pass: D!c@#$%^&*19)

ii)	JPCIP: (10.4.x.y)
(1)	User1: dicservices\odcrouser1 (pass: m923DxfvVr12)
(2)	User2: dicservices\odcrouser2 (pass: D!c@#$%^&*19)

iii)	Staging: (10.2.x.y) 
(1)	User1: dicservices\odcrouser1 (pass: m923DxfvVr12)
(2)	User2: dicservices\odcrouser2 (pass: D!c@#$%^&*19)

Notes: This process is applied for SQLMI systems


---------------------------------------------------------DiLabel Service/Web Pro QA----------------------------------------------------------------------------------------
PRODUCTION:
Production Server: 172.10.15.60 – DB Production: 172.10.15.61
-	Version 1 (just keep online, don’t maintain): 
o	Service URL: https://dilabel.dicentral.com/DiLabelService.svc 
o	Service Folder: D:\inetpub\wwwroot\DiLabelService\Service
o	Web Client URL: http://dilabel.dicentral.com:8080/ 
o	Web Client Folder: D:\inetpub\wwwroot\DiLabelService\Client 
-	Version 2 (update and maintain on this version): 
o	Service URL: https://dilabel.dicentral.com:8010/DiLabelService.svc 
o	Service Folder: D:\inetpub\wwwroot\DiLabelService\DiLabel_2.0\Service
o	Web Client URL: http://dilabel.dicentral.com:8088/ 
o	Web Client Folder: D:\inetpub\wwwroot\DiLabelService\DiLabel_2.0\Client

Test Server: DiWeb5test, DiWeb6test – DB Test: DB2 
-	Version 2 only: 
o	Service URL: http://diwebctest.dicentral.com:8010/dilabelservice.svc 
o	Service Folder: D:\inetpub\wwwroot\DiService\DiLabel\Service
o	Web Client URL: http://diwebctest.dicentral.com:8080/  
o	Web Client Folder: D:\inetpub\wwwroot\DiService\DiLabel\Client

\\172.10.75.40\ClusteredCIP\DiLabel\lbls

https://forms.office.com/Pages/ResponsePage.aspx?Host=Teams&lang=%7Blocale%7D&groupId=%7BgroupId%7D&tid=%7Btid%7D&teamsTheme=%7Btheme%7D&upn=%7Bupn%7D&id=cT2Dlfa42ECdt-RI_HLq54SyDXenOH5PkGpQFgzjK-BUMDlXMzM3VkpPT0pOTldJVkMxNU5ZUlZKOC4u

Public: http://cipdev.dicentral.com.vn:3400/
Internal: http://cipdev.dicentral.com.vn:3500/

The appointment's start and end times should be always divisible by the "15 minutes" interval.

MetricIgnoreFeature SKYJACK
http://dimetrics.dicentral.com/MetricManager/MetricIgnoreFeature.aspx?token=m%2BpNuU7v1rh%2BkfzlsAAhavzC%2BDXCtdpe1z%2FXk6kH3eljRJSPXS5rPlNdJx3Mb2DKOtFMUiyn15eK1t17YeYTc02d0UOgEVzoU35CDiLihUs1jIIheaM6uQ%3D%3D

--------------------------------------------------Absent Metrics Later 997 ACK----------------------------------------------------------------

  SELECT DateDiff(minute, sent_date,ack_date), c.customer_name, c.customer_id, i.trans_id,
                                  i.doc_id ,
                                   int_cntl_no  ,  i.sent_date as SentReceivedDate, i.outboxid as InOutBoxId, 'outbox_qr2_2021' as TableName, i.out_date as InOutDate
                                    ,i.doc_type ,i.ack_date AS ACKDate,
                                   ( select customer_isa from customer_info where customer_id = i.custid) as SenderIsaId, c.customer_isa AS ReceiverIsaId
                                   , i.gr_cntl_no , i.trans_cntl_no 
                                   FROM outbox_qr2_2021 i(NOLOCK) 
                                  INNER JOIN customer_info c(NOLOCK)on i.to_custid = c.customer_id 
                                  WHERE i.outboxid = '615231'  
                                 -- and ( ack_date is null 
                                   --  or (ack_date is not null and DateDiff(minute, sent_date,ack_date) >  3*34*60  ) 
                                --   )
  SELECT c.customer_name, c.customer_id, i.trans_id,
                                  i.doc_id ,
                                   int_cntl_no  ,  i.sent_date as SentReceivedDate, i.outboxid as InOutBoxId, 'outbox_qr2_2021' as TableName, i.out_date as InOutDate
                                    ,i.doc_type ,i.ack_date AS ACKDate,
                                   ( select customer_isa from customer_info where customer_id = i.custid) as SenderIsaId, c.customer_isa AS ReceiverIsaId
                                   , i.gr_cntl_no , i.trans_cntl_no 
                                   FROM outbox_qr2_2021 i(NOLOCK) 
                                  INNER JOIN customer_info c(NOLOCK)on i.to_custid = c.customer_id 
                                  WHERE i.outboxid = '615231'  
                                  and ( ack_date is null  )

----------------------------------------------------------Flow Dimetrics Full ----------------------------------------------------------------------------------------------
Flow  Import DiMetrics:
Flow CIP : - path : ImportData
			- import từ DB DiASCIIR9 -> bảng Dim					
		    - có check hold,
			- có absent metric
			- get metric with customerid of DOC
			- khi vi phạm rule : send mail
			
Flow Apex(Edi Extract) :- path : ImportDataNoASCII 
			- import từ DB DiASCIIR9_Rep ->  bảng Dim
			- ko có check hold
			- có absent metric
			-  if (isInbox == "Y")
                    {
                        CustomerID = receiverID;
                        ParticipantNo = senderID;
                    }
                    else
                    {
                        CustomerID = senderID;
                        ParticipantNo = receiverID;
                    }
			- get metric with customerid of DOC
			- khi vi phạm rule : send mail
       Customersupport: DownloadOutbound = N; AsciiToDb= N (business logic) right flow
			Current Setup: Downloadoutbound = N; AsciiToDb = Y (use diunitemap R9) wrong flow but work EDIEXtract. Because DiMetrics use EDI Extract Service map data to DB DiASCIIR9_Rep
Expected Result: DownloadOutbound = N; AsciiToDb= N (business logic) right flow EDI Extract

luồng All HV: - path : ImportDataByInoutboxID 
			- import từ DB DiASCIIR9_Rep ->  bảng DIMetric
			- ko check hold
			- có absend metric
			- CustomerId : 9999
			- get metric with customerid = 9999
			- khi vi phạm rule :call API bên diAlert/Sendmail
-----------------------------------------------------------------------------------------------------Server DEV------------------------
DiAutomotive Server
SQL DB
172.16.3.92
user
diconnect / di@AM123$456

DiMetrics Reconcilation .net core
admin@dicentral.com
1qazZAQ!

https://cipfedev.dicentral.com.vn:8101/supportcrm/Login.aspx
login account: ttrinh / trinhu1

local\diweb 1199@Dic! 

https://docs.angularjs.org/tutorial/step_00
co
http://qacip.dicentral.com:8082/Default.aspx#
tuannguyen / tuannguyen

https://app3.smartturn.com/User/Login
admin@testing.com/Test.123
superuser@dicentral.com
dicatalog@1199

http://172.10.1.48/customer_support/customer/profile.asp?customer_id=18907
khoatran/123456

http://172.10.2.45/customer_support/main.asp
dungkhacnguyen/dicentral

http://diweb5test.dicentral.com/
diallusers/di17625;mai
drupp/dicentral

CIPDEV VN:

http://diwebtestvn.dicentral.com.vn
diallusers/diallusers
vntest/vntest1

http://172.16.3.69:8082/Default.aspx
diadmin/123456

http://172.16.3.69:8082/Default.aspx
thuynguyen/thuynguyen

---------------------------------------File Zilla Upload File 850 856 810,...---------------------------------------------------------------------------------------
filezilla:
172.16.3.69 ;
832: alf3182538/ach35390 ; 
850: DiAnonymous / 123456

QACIP:
ftp://qacip.dicentral.com
alf3182538/ach35390

Eastwood
IwKDps/dJJtGt

QACIP ALL HUBS ALL VENDORSs
user: directgxs
pass: directgxs
host: ftp://qacip.dicentral.com

Quick Cable Corporation@ftp
user: qui6708051
pass: dicentral

-----------------------------------------------Remote Desktop Server PRO QA Azure--------------------------------------------------------------------------
PRODUCTION 
DataImportQueue Service
Import Engine Service
Metric Engine Service
172.10.3.81
172.10.3.80
sky18355/sky062016
PRO SKYJACK login
sky18355/D!central2

SSMS:
- dicsqmmitest : didbro/s7rRkskn
Azure Dev & Test (Sing)
Remote Login 172.16.3.89 

Azure Staging
10.2.11.24
10.2.11.25

Dimetrics DB
Source: dicstagingdb
odcro\Dicentral@139
dicentral\odcrouser1 (pass: m923DxfvVr)
dicentral\odcrouser2 (pass: D!c@#$%^&*19)

PRODUCTION
sky18355/sky062016

Azure Dev  Test:
dicsqmmitest
didbro/s7rRkskn

DiAutomative Login QACIP    
https://diwebctest.dicentral.com:8043/
Dic8808237/Dicentral@1

NLB DiMetrics Production
DIMETRICNLB1 (172.10.3.80)
DIMETRICNLB2 (172.10.3.81)

NLB DiMetrics QACIP
172.10.97.21  
172.10.97.22
