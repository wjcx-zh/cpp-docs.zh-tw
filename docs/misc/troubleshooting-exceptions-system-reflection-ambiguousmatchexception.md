---
title: "疑難排解例外狀況：System.Reflection.AmbiguousMatchException | Microsoft Docs"
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
  - "System.Reflection.AmbiguousMatchException 例外狀況"
  - "AmbiguousMatchException 例外狀況"
ms.assetid: f92b5c51-42b6-4c2e-83df-0d598b3b41c4
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Reflection.AmbiguousMatchException
繫結至方法，導致一個以上的方法符合繫結準則時，所擲回的例外狀況。  
  
## 備註  
 如果應用程式呼叫類別，且無法決定使用哪個類別或多載類別時，便會擲回 <xref:System.Reflection.AmbiguousMatchException>。 繫結會嘗試根據參數的數目和參數的型別，找出適合使用的類別。 如果找到多個可接受的類別，就會擲回此例外狀況。  
  
## 請參閱  
 <xref:System.Reflection.AmbiguousMatchException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)