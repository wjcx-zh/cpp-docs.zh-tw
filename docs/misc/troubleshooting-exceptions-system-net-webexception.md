---
title: "疑難排解例外狀況：System.Net.WebException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "WebException 類別"
ms.assetid: 6cd69a2c-c52b-420d-be47-a4e34eaec6f3
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Net.WebException
透過可外掛式通訊協定存取網路時發生錯誤，就會擲回 <xref:System.Net.WebException> 例外狀況。  
  
## 相關秘訣  
 **請檢查例外狀況的 Response 屬性來判斷要求為何失敗。**  
 當 <xref:System.Net.WebException> 類別的子系擲回 <xref:System.Net.WebRequest> 例外狀況時，<xref:System.Net.WebException.Response%2A> 屬性會將網際網路回應提供給應用程式。  
  
 **請檢查例外狀況的 Status 屬性來判斷要求為何失敗。**  
 例外狀況的 <xref:System.Net.WebException.Status%2A> 屬性會提供該錯誤的狀態資訊。 如需詳細資訊，請參閱<xref:System.Net.WebExceptionStatus>。  
  
 **如果逐步執行 XML Web Service 時造成逾時，請將 XML Web Service 呼叫的逾時值設定為無限。**  
 如需詳細資訊，請參閱[錯誤：偵錯 Web 服務時逾時](../Topic/Error:%20Timeout%20While%20Debugging%20Web%20Services.md)。  
  
## 請參閱  
 <xref:System.Net.WebException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [如何：使用 WebRequest 類別傳送資料](../Topic/How%20to:%20Send%20Data%20Using%20the%20WebRequest%20Class.md)   
 [如何：使用 WebRequest 類別要求資料](../Topic/How%20to:%20Request%20Data%20Using%20the%20WebRequest%20Class.md)   
 [如何：擷取符合 WebRequest 的通訊協定特定 WebResponse](../Topic/How%20to:%20Retrieve%20a%20Protocol-Specific%20WebResponse%20that%20Matches%20a%20WebRequest.md)