---
title: "編譯器警告 (層級 1) CS1584 | Microsoft Docs"
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
  - "CS1584"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1584"
ms.assetid: 56c8f9bf-4cce-4269-b573-d60e5b11f9ab
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1584
'member' 上 XML 註解的 cref 屬性 'invalid\_syntax' 語法不正確  
  
 其中一個傳遞給標記以進行文件註解的參數語法無效。 如需詳細資訊，請參閱[建議使用的文件註解標籤](../Topic/Recommended%20Tags%20for%20Documentation%20Comments%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS1584：  
  
```  
// CS1584.cs // compile with: /W:1 /doc:CS1584.xml /// <remarks>Test class</remarks> public class Test { /// <remarks>Called in <see cref="Test.Mai()n"/>.</remarks>   // CS1584 // try the following line instead // /// <remarks>Called in <see cref="Test.Main()"/>.</remarks> public static void Test2() {} /// <remarks>Main method</remarks> public static void Main() {} }  
```