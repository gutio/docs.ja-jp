---
title: "JSON および XML 形式の AJAX サービスのサンプル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# JSON および XML 形式の AJAX サービスのサンプル
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用して、JSON \(JavaScript Object Notation\) または XML データのいずれかを返す AJAX \(Asynchronous JavaScript and XML\) サービスを作成する方法について説明します。AJAX サービスには、Web ブラウザー クライアントから JavaScript コードを使用してアクセスできます。このサンプルは、「[基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)」のサンプルに基づいています。  
  
 他の AJAX サンプルとは異なり、このサンプルでは ASP.NET AJAX および <xref:System.Web.UI.ScriptManager> コントロールを使用しません。追加の構成を行うと、JavaScript を使用して HTML ページから [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX サービスにアクセスできます。このシナリオを次に示します。ASP.NET AJAX と共に [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用する例については、「[AJAX Samples](http://msdn.microsoft.com/ja-jp/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)」を参照してください。  
  
 このサンプルでは、JSON と XML 間で操作の応答のタイプを切り替える方法を示します。この機能は、サービスが ASP.NET AJAX または HTML\/JavaScript クライアント ページでアクセスできるように構成されているかどうかにかかわらず使用できます。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 ASP.NET AJAX 以外のクライアントを使用するには、.svc ファイルで <xref:System.ServiceModel.Activation.WebServiceHostFactory> \(<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ではありません\) を使用します。<xref:System.ServiceModel.Activation.WebServiceHostFactory> によって、<xref:System.ServiceModel.Description.WebHttpEndpoint> 標準エンドポイントがサービスに追加されます。エンドポイントは .svc ファイルに相対する空のアドレス位置に作成されます。つまり、サービスのアドレスは、操作名以外の追加のサフィックスのない http:\/\/localhost\/ServiceModelSamples\/service.svc になります。  
  
```html  
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>  
  
```  
  
 Web.config 内の次のセクションを使用して、エンドポイントに対する構成変更を追加できます。追加の変更が不要な場合は、このセクションを削除できます。  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name="" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
  
```  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint> の既定のデータ形式は XML であるのに対し、<xref:System.ServiceModel.Description.WebScriptEndpoint> の既定のデータ形式は JSON です。詳細については、「[ASP.NET を使用せずに WCF AJAX サービスを作成する方法](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)」を参照してください。  
  
 次に示すサンプル内のサービスは、2 つの操作が設定された標準の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスです。どちらの操作でも <xref:System.ServiceModel.Web.WebGetAttribute> または <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性に <xref:System.ServiceModel.Web.WebMessageBodyStyle> の本文スタイルが必要です。この本文スタイルは、`webHttp` 動作に固有で、JSON\/XML データ形式の切り替えに影響しません。  
  
```  
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```  
  
 この操作の応答形式は、XML として指定されています。これは、[\<webHttp\>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) 動作の既定の設定です。ただし、応答形式を明示的に指定することをお勧めします。  
  
 その他の操作では `WebInvokeAttribute` 属性を使用し、応答に XML ではなく JSON を明示的に指定します。  
  
```  
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```  
  
 どちらの場合でも、操作により、標準の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] データ コントラクト型である複合型 `MathResult` が返されます。  
  
 クライアント Web ページ XmlAjaxClientPage.htm には、ページ上の **\[Perform calculation \(return JSON\)\]** または **\[Perform calculation \(return XML\)\]** ボタンをクリックすると上記の 2 つの操作のどちらかを呼び出す JavaScript コードが含まれています。サービスを呼び出すコードによって JSON 本文が作成され、HTTP POST を使用して送信されます。「[基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)」のサンプルや、ASP.NET AJAX を使用するその他のサンプルとは異なり、要求は JavaScript で手動で作成します。  
  
```  
// Create HTTP request  
var xmlHttp;  
// Request instantiation code omitted…  
// Result handler code omitted…  
  
// Build the operation URL  
var url = "service.svc/ajaxEndpoint/";  
url = url + operation;  
  
// Build the body of the JSON message  
var body = '{"n1":';  
body = body + document.getElementById("num1").value + ',"n2":';  
body = body + document.getElementById("num2").value + '}';  
  
// Send the HTTP request  
xmlHttp.open("POST", url, true);  
xmlHttp.setRequestHeader("Content-type", "application/json");  
xmlHttp.send(body);  
```  
  
 サービスが応答すると、応答はこれ以上の処理を行わずにページ上のテキスト ボックスに表示されます。これは、使用される XML および JSON データ形式を直接確認できるように、デモンストレーションの目的で実装されています。  
  
```  
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従って、ソリューション XmlAjaxService.sln をビルドします。  
  
3.  http:\/\/localhost\/ServiceModelSamples\/XmlAjaxClientPage.htm に移動します \(プロジェクト ディレクトリからブラウザで XmlAjaxClientPage.htm を開かないでください\)。  
  
## 参照  
 [HTTP POST を使用する AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)