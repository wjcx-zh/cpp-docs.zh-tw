---
title: "編譯器警告 (層級 3) CS0419 | Microsoft Docs"
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
  - "CS0419"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0419"
ms.assetid: de439ad5-422f-4ed6-96d6-69dade29c7b2
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 3) CS0419
cref 屬性中有模稜兩可的參考：'Method Name1'。  已假設為 'Method Name2'，但也可能符合其他多載，包括 'Method Name3'。  
  
 在程式碼的 XML 文件註解中，無法解析參考。 如果多載方法，或找到兩個不同的同名識別項，可能會發生這種狀況。 若要解決這個警告，請使用限定名稱以明確化參考，或使用括弧括住特定多載。  
  
 下列範例會產生 CS0419。  
  
```  
// cs0419.cs // compile with: /doc:x.xml /W:3 interface I { /// text for F(void) void F(); /// text for F(int) void F(int i); } /// text for class MyClass public class MyClass { /// <see cref="I.F"/> public static void MyMethod(int i) { } /* Try this instead: /// <see cref="I.F(int)"/> public static void MyMethod(int i) { } */ /// text for Main public static void Main () { } }  
```