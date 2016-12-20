---
title: "編譯器警告 (層級 4) CS1712 | Microsoft Docs"
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
  - "CS1712"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1712"
ms.assetid: d9a8be26-c0ba-41fa-b082-1ce4ba7724b7
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 4) CS1712
在 XML 註解中，類型參數 '類型參數' 沒有關於 'type' 的相符 typeparam 標記 \(但其他類型參數有\)  
  
 泛型類型的文件中遺漏 **typeparam** 標記。 如需詳細資訊，請參閱[\<typeparam\>](../Topic/%3Ctypeparam%3E%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列程式碼會產生警告 CS1712。 若要解決此錯誤，請加入類型參數 S 的 **typeparam** 標記。  
  
```  
// CS1712.cs // compile with: /doc:cs1712.xml using System; class Test { public static void Main() {} /// <param name="j"> This is the j parameter.</param> /// <typeparam name="T"> This is the T type parameter.</typeparam> public void bar<T,S>(int j) {}  // CS1712 }  
```