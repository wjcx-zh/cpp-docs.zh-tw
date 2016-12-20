---
title: "疑難排解例外狀況：System.DivideByZeroException | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - "DivideByZeroException 類別"
ms.assetid: ddc79201-3ba1-455f-8496-edaad792ccf1
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.DivideByZeroException
嘗試將整數或十進位值除以零時，就會擲回 <xref:System.DivideByZeroException> 例外狀況。  
  
## 相關秘訣  
 **\[執行除法運算前請確定分母的值不是零。\]**  
 依 IEEE 運算的規則而定，將浮點數值除以零會造成無限大的正數、無限大的負數，或不是數字 \(NaN\)，。 浮點運算絕不會擲回例外狀況。  
  
## 請參閱  
 <xref:System.DivideByZeroException>   
 [Arithmetic Operators in Visual Basic](../Topic/Arithmetic%20Operators%20in%20Visual%20Basic.md)   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)