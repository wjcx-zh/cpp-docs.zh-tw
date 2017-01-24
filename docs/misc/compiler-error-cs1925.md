---
title: "編譯器錯誤 CS1925 | Microsoft Docs"
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
  - "CS1925"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1925"
ms.assetid: b60806a5-2ccf-47f5-873b-7ac2292fdb54
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1925
無法使用集合初始設定式來初始化類型 'type' 的物件。  
  
 集合初始設定式只能用於符合特定準則的集合類別。 如需詳細資訊，請參閱[物件和集合初始設定式](../Topic/Object%20and%20Collection%20Initializers%20\(C%23%20Programming%20Guide\).md)。 當您嘗試使用巢狀於集合初始設定式內之陣列初始設定式的簡短形式時，也會產生這個錯誤。  
  
### 更正這個錯誤  
  
1.  呼叫物件的建構函式和方法來初始化物件。  
  
## 範例  
 下列程式碼會產生 CS1925：  
  
```  
// cs1925.cs public class Student { public int[] Scores; } class Test { static void Main(string[] args) { Student student = new Student { Scores = { 1, 2, 3 } }; // CS1925 } }  
```