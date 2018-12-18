---
title: Expose objects as web services 
description: Publish [!INCLUDE[d365fin](includes/d365fin_md.md)] objects as web services, they are immediately available on the network.
author: edupont04

ms.prod: "dynamics-nav-2018"
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords:
ms.date: 09/01/2017
ms.author: edupont

---
# How to: Publish a Web Service
Web services are a lightweight way to make application functionality available to a variety of external systems and users. [!INCLUDE[d365fin](includes/d365fin_md.md)] includes an number of objects that are exposed as web services by default due to integration with other Microsoft services, but you can also add other web services.  

You can set up a web service in the Windows client or in the Web client. You must then publish the web service so that it is available to service requests over the network. Users can discover web services by pointing a browser at the server location and requesting a list of available services. When you publish a web service, it is immediately available over the network for authenticated users. All authorized users can access metadata for web services, but only users who have sufficient permissions can access actual data.

## Creating and Publishing a Web Service  
 The following steps explain how to create and publish a web service.  

#### To create and publish a web service  

1.  Choose the ![Search for Page or Report](media/ui-search/search_small.png "Search for Page or Report icon") icon, enter **Web Services**, and then choose the related link.  

2.  In the **Web Services** page, choose **New**. [!INCLUDE[tooltip-inline-tip](includes/tooltip-inline-tip_md.md)]  

    > [!NOTE]  
    >  **Codeunit** and **Page** are valid types for SOAP web services. **Page** and **Query** are valid types for OData web services.  
    Also, if the database contains multiple companies, you can choose an object ID that is specific to one of the companies.  
    Finally, the service name is visible to consumers of your web service and is the basis for identifying and distinguishing web services, so you should make the name meaningful.

3.  Select the check box in the **Published** column.  

     When you publish the web service, in the **OData URL** and **SOAP URL** fields, you can see the URLs that are generated for the web service. You can test the web service immediately by choosing the links in the **OData URL** and **SOAP URL** fields. Optionally, you can copy the value of the field and save it for later use.  

After you publish a web service, it is available to external parties. You can verify the availability of that web service by using a browser, or you can choose the link in the **OData URL** and **SOAP URL** fields in the **Web Services** window. The following procedure illustrates how you can verify the availability of the web service for later use.  

#### To verify the availability of a web service  

1. In your browser, enter the relevant URL. The following table illustrates the types of URLs that you can enter. For SOAP web services, use the following format for your URI.  

   <table>
   <tr>
   <th>Web service type</th>
   <th>Syntax</th>
   <th>Example</th>
   </tr>
   <tr>
   <td>SOAP</td>
   <td>https://<em>Server</em>:<em>SOAPWebServicePort</em>/<em>ServerInstance</em>/WS/<em>CompanyName</em>/salesDocuments/</td>
   <td><a href="https://mycompany.financials.dynamics.com:7047/MS/WS/MyCompany/Page/salesDocuments?tenant=mycompany.financials.dynamics.com" data-raw-source="https://mycompany.financials.dynamics.com:7047/MS/WS/MyCompany/Page/salesDocuments?tenant=mycompany.financials.dynamics.com">https://mycompany.financials.dynamics.com:7047/MS/WS/MyCompany/Page/salesDocuments?tenant=mycompany.financials.dynamics.com</a></td>
   </tr>
   <tr>
   <td>OData</td>
   <td>https://<em>Server</em>:<em>ODataWebServicePort</em>/<em>ServerInstance</em>/OData/Company(&#39;<em>CompanyName</em>&#39;)</td>
   <td>https://MyCompany.financials.dynamics.com:7048/MS/OData/Company(&#39;MyCompany&#39;)/salesDocuments?tenant=MyCompany.financials.dynamics.com

        The company name is case-sensitive.</td>
   </tr>
   </table>

2. Review the information that is displayed in the browser. Verify that you can see the name of the web service that you have created.  

   When you access a web service, and you want to write data back to [!INCLUDE[d365fin](includes/d365fin_md.md)], you must specify the company name. You can specify the company as part of the URI as shown in the examples, or you can specify the company as part of the query parameters. For example, the following URIs point to the same OData web service and are both valid URIs.  

```  
https://localhost:7048/server/OData/Company('CRONUS International Ltd.')/Customer  
```  

```  
https://localhost:7048/server/OData/Customer?company='CRONUS International Ltd.'  
```  

## See Also  
[Setup and Administration in Dynamics NAV](admin-setup-and-administration.md)  
