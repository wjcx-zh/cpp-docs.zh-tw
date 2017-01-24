---
title: "編譯器錯誤 CS0176 | Microsoft Docs"
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
  - "CS0176"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0176"
ms.assetid: 783c13d8-5ac3-4aeb-bd63-0468cb05550d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0176
無法以執行個體參考來存取靜態成員 'member'; 請以類型名稱限定它  
  
 類別名稱只能用來限定[靜態](../Topic/static%20\(C%23%20Reference\).md)變數；執行個體名稱不能是限定詞。 如需詳細資訊，請參閱[靜態類別和靜態類別成員](../Topic/Static%20Classes%20and%20Static%20Class%20Members%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0176：  
  
```  
// CS0176.cs public class MyClass2 { public static int num; } public class Test { public static void Main() { MyClass2 mc2 = new MyClass2(); int i = mc2.num;   // CS0176 // try the following line instead // int i = MyClass2.num; } }  
  
```