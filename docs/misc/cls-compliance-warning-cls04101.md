---
title: "CLS 符合性警告 CLS04101 | Microsoft Docs"
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
  - "CLS04101"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04101"
ms.assetid: 5ad21eb4-0c6e-4629-bc4a-af274f8a8d90
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS04101
屬性應該是類型 'System::Attribute'，或從它繼承而來  
  
 請確定套用至建構函式參數的所有屬性都有類型 'System.Attribute'，或繼承自它的類型。  
  
 如需公用語言子集 \(Common Language Subset, CLS\) 符合性檢查的詳細資訊，請參閱[符合 CLS 標準的組件](http://msdn.microsoft.com/zh-tw/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下列宣告 \(使用 MSIL 組件語言\) 顯示何種狀況可能導致 CLS04101：  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object { .method public specialname rtspecialname instance void  .ctor() cil managed  
```  
  
 讓屬性衍生自 System::Attribute 即可解決警告：  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object { .method public specialname rtspecialname instance void  .ctor() cil managed  
```