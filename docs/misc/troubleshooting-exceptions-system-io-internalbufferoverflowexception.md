---
title: "疑難排解例外狀況：System.IO.InternalBufferOverflowException | Microsoft Docs"
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
  - "InternalBufferOverflowException 類別"
ms.assetid: 1f58ca15-c4e4-4af9-9a3d-42d2cf919cbe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.IO.InternalBufferOverflowException
內部緩衝區溢位時，就會擲回 <xref:System.IO.InternalBufferOverflowException> 例外狀況。  
  
## 相關秘訣  
 **使用 FileSystemWatcher 時，請篩選掉不必要的變更告知。**  
 當您在檔案系統監看員中收到檔案變更的通知時，系統會將這些變更儲存在元件所建立的緩衝區中，然後傳遞至應用程式開發介面 \(API\)。 如果短時間內有太多變更，緩衝區會溢位而產生 <xref:System.IO.InternalBufferOverflowException> 例外狀況，這會遺失所有變更。 若要防止緩衝區溢位，請使用 <xref:System.IO.FileSystemWatcher.NotifyFilter%2A> 和 <xref:System.IO.FileSystemWatcher.IncludeSubdirectories%2A> 屬性篩選掉不必要的變更通知。 如需詳細資訊，請參閱<xref:System.IO.FileSystemWatcher>。  
  
## 備註  
 您也可以透過 <xref:System.IO.FileSystemWatcher.InternalBufferSize%2A> 屬性增加內部緩衝區的大小。 但是，增加內部緩衝區的大小會影響效能，因此緩衝區越小越好。  
  
## 請參閱  
 <xref:System.IO.InternalBufferOverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)