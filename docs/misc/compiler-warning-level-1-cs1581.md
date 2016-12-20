---
title: "編譯器警告 (層級 1) CS1581 | Microsoft Docs"
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
  - "CS1581"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1581"
ms.assetid: b7ac7586-a724-492c-887f-795af1c3bcc4
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1581
XML 註解 cref 屬性中的傳回類型無效  
  
 當嘗試參考方法時，編譯器偵測到錯誤，因為傳回類型無效。  
  
## 範例  
 下列範例會產生 CS1581：  
  
```  
// CS1581.cs // compile with: /W:1 /doc:x.xml /// <summary>help text</summary> public class MyClass { /// <summary>help text</summary> public static void Main() { } /// <summary>help text</summary> public static explicit operator int(MyClass f) { return 0; } } /// <seealso cref="MyClass.explicit operator intt(MyClass)"/>  // CS1581 // try the following line instead // /// <seealso cref="MyClass.explicit operator int(MyClass)"/> public class MyClass2 { }  
```