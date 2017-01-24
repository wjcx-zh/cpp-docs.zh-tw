---
title: "CLS 符合性警告 CLS04106 | Microsoft Docs"
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
  - "CLS04106"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04106"
ms.assetid: a74e4cb7-c96a-4673-bf11-c2ff3c4b02f1
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS04106
屬性應該是類型 'System::Attribute'，或從它繼承而來  
  
 為了符合 CLS 標準，自訂屬性必須繼承自 System::Attribute。  未繼承自 System::Attribute 的屬性已套用至函式。  
  
 下列宣告 \(使用 MSIL 組件語言\) 顯示何種狀況可能導致 CLS04106：  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 然後顯示使用屬性的函式：  
  
```  
.custom instance void MyAttribute::.ctor(int32) = ( 01 00 01 00 00 00 00 00 )  
```  
  
 讓屬性衍生自 System::Attribute 即可解決警告：  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```