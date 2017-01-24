---
title: "編譯器錯誤 CS0154 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0154"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0154"
ms.assetid: 815150da-09b4-4593-825f-1dd435c92da8
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0154
無法於此內容中使用屬性或索引子 'property'，因為其欠缺 get 存取子  
  
 嘗試使用[屬性](../Topic/Using%20Properties%20\(C%23%20Programming%20Guide\).md)失敗，因為屬性中沒有定義 get 存取子方法。 如需詳細資訊，請參閱[欄位](../Topic/Fields%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0154：  
  
```  
// CS0154.cs public class MyClass2 { public int i { set { } // uncomment the get method to resolve this error /* get { return 0; } */ } } public class MyClass { public static void Main() { MyClass2 myClass2 = new MyClass2(); int j = myClass2.i;   // CS0154, no get method } }  
```