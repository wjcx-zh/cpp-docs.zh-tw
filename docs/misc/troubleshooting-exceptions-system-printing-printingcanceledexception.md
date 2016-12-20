---
title: "疑難排解例外狀況：System.Printing.PrintingCanceledException | Microsoft Docs"
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
  - "PrintingCanceledException 例外狀況"
  - "System.Printing.PrintingCanceledException 例外狀況"
ms.assetid: bec418d6-f168-4a73-962f-5ee0427600b6
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Printing.PrintingCanceledException
當程式碼嘗試存取已取消的列印工作時，就會發生 <xref:System.Printing.PrintingCanceledException> 例外狀況。  
  
## 備註  
 如果您要建立包括列印功能且可取消列印工作的 Windows Presentation Foundation \(WPF\) 應用程式，請務必正確處理這個例外狀況。 未處理的這類例外狀況可能導致 Windows Presentation Foundation 應用程式停止回應。  
  
## 請參閱  
 <xref:System.Printing.PrintingCanceledException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)