---
title: "編譯器錯誤 CS0026 | Microsoft Docs"
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
  - "CS0026"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0026"
ms.assetid: 8767fbc1-8ba7-4e88-a9f9-7e620411882b
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0026
關鍵字 'this' 在靜態屬性、靜態方法或靜態欄位初始設定式中無效。  
  
 [this](../Topic/this%20\(C%23%20Reference\).md) 關鍵字參考的物件是某個類型的執行個體。 由於靜態方法與任何包含類別執行個體皆無關，因此 "this" 關鍵字是無意義且不被允許的。 如需詳細資訊，請參閱 [靜態類別和靜態類別成員](../Topic/Static%20Classes%20and%20Static%20Class%20Members%20\(C%23%20Programming%20Guide\).md) 與 [物件](../Topic/Objects%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0026：  
  
```  
// CS0026.cs public class A { public static int i = 0; public static void Main() { // CS0026 this.i = this.i + 1; // Try the following line instead: // i = i + 1; } }  
```