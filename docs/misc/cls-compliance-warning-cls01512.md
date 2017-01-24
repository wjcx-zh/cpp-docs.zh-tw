---
title: "CLS 符合性警告 CLS01512 | Microsoft Docs"
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
  - "CLS01512"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01512"
ms.assetid: 15822eb3-43b1-4d58-a22d-9532e5820008
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS01512
varargs 條件約束不是 CLS 的一部分  
  
 varargs 條件約束不是 Common Language Subset \(CLS\) 的一部分。  CLS 所支援的唯一呼叫慣例是標準 Managed 呼叫慣例。  
  
 如需 CLS 符合性檢查的詳細資訊，請參閱[符合 CLS 標準的組件](http://msdn.microsoft.com/zh-tw/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下列函式宣告 \(使用 MSIL 組件語言\) 顯示何種狀況可能導致 CLS01512：  
  
```  
.method public specialname rtspecialname static vararg void  .cctor() cil managed  
```  
  
 移除 **vararg** 關鍵字，即可解決這個警告：  
  
```  
.method public specialname rtspecialname static void  .cctor() cil managed  
```