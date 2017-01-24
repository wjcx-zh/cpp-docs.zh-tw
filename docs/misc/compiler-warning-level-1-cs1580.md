---
title: "編譯器警告 (層級 1) CS1580 | Microsoft Docs"
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
  - "CS1580"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1580"
ms.assetid: ffd1b6d7-6cab-47e3-b7fe-c79cb435cddf
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1580
XML 註解 cref 屬性中的參數 'parameter number' 類型無效  
  
 當嘗試參考多載格式的方法時，編譯器偵測到語法錯誤。 一般而言，這表示已指定參數名稱，而非類型。 產生的 XML 檔案中會出現格式不正確的程式行。  
  
 下列範例會產生 CS1580：  
  
```  
// CS1580.cs // compile with: /W:1 /doc:x.xml using System; /// <seealso cref="Test(i)"/>   // CS1580 // try the following line instead // /// <seealso cref="Test(int)"/> public class MyClass { /// <summary>help text</summary> public static void Main() { } /// <summary>help text</summary> public void Test(int i) { } /// <summary>help text</summary> public void Test(char i) { } }  
```