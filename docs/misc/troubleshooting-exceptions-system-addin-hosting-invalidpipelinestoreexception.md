---
title: "疑難排解例外狀況：System.AddIn.Hosting.InvalidPipelineStoreException | Microsoft Docs"
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
  - "InvalidPipelineStoreException 例外狀況"
  - "System.AddIn.Hosting.InvalidPipelineStoreException 例外狀況"
ms.assetid: d12556bc-5cfd-481c-a27b-46ee2571e646
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.AddIn.Hosting.InvalidPipelineStoreException
當找不到目錄，而且使用者沒有存取管線根路徑或增益集路徑的權限時，就會擲回 <xref:System.AddIn.Hosting.InvalidPipelineStoreException> 例外狀況。  
  
## 備註  
 這個例外狀況與 <xref:System.IO.DirectoryNotFoundException> 不同，它不會提供任何路徑資訊。 這可防止惡意使用者蓄意指定錯誤的路徑，並使用例外狀況所傳回的資訊來判斷實際路徑。  
  
 下列建置及更新增益集和管線資訊存放區的探索方法都會擲回這個例外狀況：<xref:System.AddIn.Hosting.AddInStore.FindAddIns%2A>、<xref:System.AddIn.Hosting.AddInStore.Rebuild%2A>、<xref:System.AddIn.Hosting.AddInStore.RebuildAddIns%2A>、<xref:System.AddIn.Hosting.AddInStore.Update%2A> 和 <xref:System.AddIn.Hosting.AddInStore.UpdateAddIns%2A>。  
  
## 請參閱  
 <xref:System.AddIn.Hosting.InvalidPipelineStoreException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)