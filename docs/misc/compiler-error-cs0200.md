---
title: "編譯器錯誤 CS0200 | Microsoft Docs"
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
  - "CS0200"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0200"
ms.assetid: 1990704a-edfa-4dbd-8477-d9c7aae58c96
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0200
無法指派屬性或索引子 'property' \-\- 其為唯讀  
  
 已嘗試指派值給[屬性](../Topic/Using%20Properties%20\(C%23%20Programming%20Guide\).md)，但此屬性沒有 set 存取子。 請加入 set 存取子來解決此錯誤。 如需詳細資訊，請參閱[如何：宣告及使用讀寫屬性](../Topic/How%20to:%20Declare%20and%20Use%20Read%20Write%20Properties%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0200：  
  
```  
// CS0200.cs public class MainClass { // private int _mi; int I { get { return 1; } // uncomment the set accessor and declaration for _mi /* set { _mi = value; } */ } public static void Main () { MainClass II = new MainClass(); II.I = 9;   // CS0200 } }  
```