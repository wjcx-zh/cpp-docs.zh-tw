---
title: "編譯器錯誤 CS0075 | Microsoft Docs"
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
  - "CS0075"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0075"
ms.assetid: 5084d260-705e-4ff5-8f7a-7f74052fcbbb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0075
要做轉型的負值必須置於括號之內  
  
 如果您使用會識別預先定義之類型的關鍵字來將類型轉型，則不需要括弧。 否則，您必須加上括弧，因為 \(x\) –y 不會視為轉型運算式。 取自 C\# 規格的第 7.6.6 節：  
  
 *從去除混淆規則得出，如果 x 和 y 是識別項，\(x\)y、\(x\)\(y\) 和 \(x\)\(\-y\) 是轉型運算式，但 \(x\)\-y 不是，即使 x 識別類型也一樣。 不過，如果 x 是識別預先定義之類型 \(例如 int\) 的關鍵字，則四種形式全都是轉型運算式 \(因為這類關鍵字本身不可能是運算式\)。*  
  
 下列程式碼會產生 CS0075：  
  
```  
// CS0075 namespace MyNamespace { enum MyEnum { } public class MyClass { public static void Main() { // To fix the error, place the negative // values below in parentheses int i = (System.Int32) - 4; //CS0075 MyEnum e = (MyEnum) - 1;    //CS0075 System.Console.WriteLine(i); //to avoid warning System.Console.WriteLine(e); //to avoid warning } } }  
```  
  
## 請參閱  
 [轉型和類型轉換](../Topic/Casting%20and%20Type%20Conversions%20\(C%23%20Programming%20Guide\).md)