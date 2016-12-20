---
title: "疑難排解例外狀況：System.IO.FileLoadException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "FileLoadException 類別"
ms.assetid: 6b4519e3-4d29-4031-8aec-c2735b4ee16d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.IO.FileLoadException
當您找到 Managed 組件卻無法載入時，就會擲回 <xref:System.IO.FileLoadException> 例外狀況。  
  
## 相關秘訣  
 **請確定檔案是有效的 .NET Framework 組件。**  
 如果該檔案不是有效的 .NET Framework 組件，就會擲回這個例外狀況。 如需詳細資訊，請參閱<xref:System.Reflection.Assembly>。  
  
 **檢查以確定未使用兩個不同的辨識項，載入組件或模組兩次。**  
 所謂的辨識項是一組資訊，由輸入的安全性原則決策所構成，例如要將那些權限授與給程式碼。 如需詳細資訊，請參閱 <xref:System.EnterpriseServices.Internal.Publish.GacRemove%2A>和 <xref:System.Reflection.Assembly.Evidence%2A>。  
  
 **如果使用 RegisterAssembly 或 UnregisterAssembly 方法，請檢查該組件的名稱，以確定長度沒有超過 MAX\_PATH 字元。**  
 組件名稱的長度不能超過 MAX\_PATH。 如需詳細資訊，請參閱<xref:System.EnterpriseServices.Internal.IComSoapPublisher.RegisterAssembly%2A>與<xref:System.EnterpriseServices.Internal.IComSoapPublisher.UnRegisterAssembly%2A>。  
  
 **載入附屬組件時，請確定指定的 CultureInfo 需符合該檔案的 CultureInfo。**  
 附屬組件包含了當地語系化資源，這些資源中含有不能當地語系化的可執行程式碼。附屬組件也包含了單一文化的資源，用以做為預設或中性文化。 如需詳細資訊，請參閱<xref:System.Reflection.Assembly.GetSatelliteAssembly%2A>。  
  
## 請參閱  
 <xref:System.IO.FileLoadException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)