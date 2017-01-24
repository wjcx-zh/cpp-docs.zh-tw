---
title: "編譯器錯誤 CS0119 | Microsoft Docs"
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
  - "CS0119"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0119"
ms.assetid: 048924f1-378f-4021-bd20-299d3218f810
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0119
'construct1\_name' 是 'construct1'，其在指定內容中無效。  
  
 編譯器偵測到非預期的建構，如下所示：  
  
-   類別建構函式不是條件陳述式中的有效測試運算式。  
  
-   已使用類別名稱 \(而非執行個體名稱\) 來參考陣列項目。  
  
-   使用方法識別項的方式就像它是結構或類別一樣  
  
## 範例  
 下列範例會產生 CS0119。  
  
```  
// CS0119.cs using System; public class MyClass { public static void Test() {} public static void Main() { Console.WriteLine(Test.x);   // CS0119 } }  
```