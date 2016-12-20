---
title: "編譯器錯誤 CS0819 | Microsoft Docs"
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
  - "CS0819"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0819"
ms.assetid: a5369e03-eb7d-4c88-b390-51304bd8d1ae
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0819
隱含類型區域變數不能有多個宣告子。  
  
 明確類型宣告中允許多個宣告子，但隱含類型變數則不允許。  
  
### 更正這個錯誤  
  
1.  在個別行上，宣告並指派每個隱含類型區域變數的值。  
  
## 範例  
 下列程式碼會產生 CS0819：  
  
```  
// cs0819.cs class A { public static int Main() { var a = 3, b = 2; // CS0819 return -1; } }  
```  
  
## 請參閱  
 [隱含類型區域變數](../Topic/Implicitly%20Typed%20Local%20Variables%20\(C%23%20Programming%20Guide\).md)