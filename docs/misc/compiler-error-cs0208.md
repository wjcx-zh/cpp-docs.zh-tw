---
title: "編譯器錯誤 CS0208 | Microsoft Docs"
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
  - "CS0208"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0208"
ms.assetid: 03534893-1522-4dab-9822-8b9ed97b3bd0
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0208
無法取得 Managed 類型 \('type'\) 的位址或大小，也無法宣告指向它的指標。  
  
 即使搭配使用 [unsafe](../Topic/unsafe%20\(C%23%20Reference\).md) 關鍵字時，也不允許取得 Managed 物件的位址、取得 Managed 物件的大小，或宣告指向 Managed 類型的指標。 Managed 類型為：  
  
-   任何參考類型  
  
-   任何包含參考類型作為欄位或屬性的結構  
  
 如需詳細資訊，請參閱[Unsafe 程式碼和指標](../Topic/Unsafe%20Code%20and%20Pointers%20\(C%23%20Programming%20Guide\).md)和 [sizeof](../Topic/sizeof%20\(C%23%20Reference\).md)。  
  
## 範例  
 下列範例會產生 CS0208：  
  
```  
// CS0208.cs // compile with: /unsafe class myClass { public int a = 98; } struct myProblemStruct { string s; float f; } struct myGoodStruct { int i; float f; } public class MyClass { unsafe public static void Main() { // myClass is a class, a managed type. myClass s = new myClass(); myClass* s2 = &s;    // CS0208 // The struct contains a string, a managed type. int i = sizeof(myProblemStruct); //CS0208 // The struct contains only value types. i = sizeof(myGoodStruct); //OK } }  
  
```  
  
## 請參閱  
 [sizeof](../Topic/sizeof%20\(C%23%20Reference\).md)