---
title: "編譯器錯誤 CS0198 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0198"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0198"
ms.assetid: 222c20f6-3f7f-4750-9f99-b5e6ae6c1271
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0198
無法對靜態唯讀欄位 'name' 的欄位進行指派 \(除非在靜態建構函式或變數初始設定式\)  
  
 [readonly](../Topic/readonly%20\(C%23%20Reference\).md) 變數的[靜態](../Topic/static%20\(C%23%20Reference\).md)使用情形必須與您想要在其中初始化它的建構函式相同。 如需詳細資訊，請參閱[靜態建構函式](../Topic/Static%20Constructors%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0198：  
  
```  
// CS0198.cs class MyClass { public static readonly int TestInt = 6; MyClass() { TestInt = 11;   // CS0198, constructor is not static and readonly field is } public static void Main() { } }  
```