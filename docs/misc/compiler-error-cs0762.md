---
title: "編譯器錯誤 CS0762 | Microsoft Docs"
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
  - "CS0762"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0762"
ms.assetid: 7cedd1af-ffe6-4ca7-82fb-faa9e98014a4
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0762
無法從方法 'method' 建立委派，因為它是無實作宣告的部分方法  
  
 部分方法不需要有實作宣告。 然而，委派需要其封裝方法具有實作。  
  
### 更正這個錯誤  
  
1.  請提供用來初始化委派之方法的實作。  
  
## 範例  
  
```  
public delegate void TestDel(); public partial class C { partial void Part(); public static int Main() { C c = new C(); TestDel td = new TestDel(c.Part); // CS0762 return 1; } }  
```