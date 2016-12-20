---
title: "疑難排解例外狀況：System.Reflection.TargetException | Microsoft Docs"
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
  - "System.Reflection.TargetException 例外狀況"
  - "TargetException 例外狀況"
ms.assetid: 88b8e4b4-f1a3-4c4a-b1ef-cac176160803
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Reflection.TargetException
嘗試叫用 \(Invoke\) 無效的目標 \(Target\) 時，所擲回的例外狀況。  
  
## 備註  
 嘗試對 null 物件叫用非靜態方法時，便會擲回 <xref:System.Reflection.TargetException>。 在呼叫端沒有成員的存取權限，或者目標沒有定義成員或其他類似情況下，都可能發生這種例外狀況。  
  
## 請參閱  
 <xref:System.Reflection.TargetException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)