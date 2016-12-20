---
title: "疑難排解例外狀況：Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CantStartSingleInstanceException 例外狀況"
  - "Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException 例外狀況"
ms.assetid: 3639f15d-9547-43da-8145-60da34782991
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException
當單一執行個體應用程式的第二個執行個體無法連接到原始執行個體時，所擲回的例外狀況。  
  
## 備註  
 可能導致本問題的原因包括：  
  
-   原始執行個體停止回應。  
  
-   應用程式沒有建立核心物件的權限。  
  
     核心物件的主檔名 \(Base Name\) 是由連接組件的 GUID、主要版本號碼，以及次要版本號碼所組成。 例如，主檔名可能是 3639f15d\-9547\-43da\-8145\-60da347829915.1。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)