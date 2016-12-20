---
title: "編譯器警告 (層級 1) CS1589 | Microsoft Docs"
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
  - "CS1589"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1589"
ms.assetid: bdc47124-93ae-4c6a-81b2-dde8ec4d0ab1
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1589
無法納入檔案 'file' 的 XML 片段 'fragment' \-\- reason  
  
 因為指定的 ***reason***，所以參考檔案 \(`file`\) 之 [\<include\>](../Topic/%3Cinclude%3E%20\(C%23%20Programming%20Guide\).md) 標記的語法 \(*fragment*\) 不正確。  
  
 將在產生的 XML 檔案中放入格式不正確的程式行。  
  
 下列範例會產生 CS1589：  
  
```  
// CS1589.cs // compile with: /W:1 /doc:CS1589_out.xml /// <include file='CS1589.doc' path='MyDocs/MyMembers[@name="test"]/' />   // CS1589 // try the following line instead // /// <include file='CS1589.doc' path='MyDocs/MyMembers[@name="test"]/*' /> class Test { public static void Main() { } }  
```