---
title: "編譯器警告 (層級 2) CS0435 | Microsoft Docs"
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
  - "CS0435"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0435"
ms.assetid: e70cd8c1-d399-4af8-8b1e-69a1de389aad
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS0435
'assembly' 中的命名空間 'namespace' 與 'assembly' 中匯入的類型 'type' 相衝突。 使用 'assembly' 中定義的命名空間。  
  
 原始程式檔 \(file\_2\) 中的命名空間與 file\_1 中匯入的類型衝突時，會發出這個警告。 編譯器會使用原始程式檔中的類型。  
  
 下列範例會產生 CS0435：  
  
 先編譯這個檔案：  
  
```  
// CS0435_1.cs // compile with: /t:library public class Util { public class A { } }  
```  
  
 然後，編譯這個檔案：  
  
```  
// CS0435_2.cs // compile with: /r:CS0435_1.dll using System; namespace Util { public class A { } } public class Test { public static void Main() { Console.WriteLine(typeof(Util.A)); // CS0435 } }  
```