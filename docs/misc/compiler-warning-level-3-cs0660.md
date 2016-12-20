---
title: "編譯器警告 (層級 3) CS0660 | Microsoft Docs"
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
  - "CS0660"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0660"
ms.assetid: 2f77b45b-c5c6-46af-abe9-002e67887896
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 3) CS0660
'class' 定義了運算子 \=\= 或運算子 \!\=，但並沒有覆寫 Object.Equals\(object o\)  
  
 編譯器偵測到使用者定義的相等或不等比較運算子，但不覆寫 **Equals** 函式。 使用者定義的相等或不等運算子暗示您也需要覆寫 **Equals** 函式。 如需詳細資訊，請參閱 [NIB \- 覆寫 Equals\(\) 和運算子 \= \= 的指導方針 \(C\# 程式設計手冊\)](http://msdn.microsoft.com/zh-tw/7e4c24c5-7693-4c45-88fb-ba5204fbcb20)。  
  
 下列範例會產生 CS0660：  
  
```  
// CS0660.cs // compile with: /W:3 /warnaserror class Test   // CS0660 { public static bool operator == (object o, Test t) { return true; } // uncomment the Equals function to resolve // public override bool Equals(object o) // { //    return true; // } public override int GetHashCode() { return 0; } public static void Main() { } }  
```