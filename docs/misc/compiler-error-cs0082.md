---
title: "編譯器錯誤 CS0082 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0082"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0082"
ms.assetid: 7612976f-de2c-4f6b-87c9-43175821650c
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0082
類型 'type' 已保留具有相同參數類型名為 'name' 的成員  
  
 屬性在編譯期間會轉譯成識別項前面有 `get_` 及\/或 `set_` 的方法。 如果定義了您自己與方法名稱發生衝突的方法，就會發生錯誤。  
  
## 範例  
 下例會產生 CS0082：  
  
```  
//cs0082.cs class MyClass { //property public int MyProp { get //CS0082 { return 1; } } //conflicting Get public int get_MyProp() { return 2; } public static int Main() { return 1; } }  
```  
  
## 請參閱  
 [屬性](../Topic/Properties%20\(C%23%20Programming%20Guide\).md)