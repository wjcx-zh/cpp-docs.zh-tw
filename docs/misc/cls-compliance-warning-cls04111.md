---
title: "CLS 符合性警告 CLS04111 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS04111"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04111"
ms.assetid: 4b445ce7-d823-4cf3-b971-1c181be5fa41
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS04111
屬性應該是類型 'System::Attribute'，或從它繼承而來  
  
 為了符合 CLS 標準，自訂屬性必須繼承自 System::Attribute。  未繼承自 System::Attribute 的屬性已套用至類型。  
  
 下列宣告 \(使用 MSIL 組件語言\) 顯示何種狀況可能導致 CLS04111：  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 讓屬性衍生自 System::Attribute 即可解決警告：  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```