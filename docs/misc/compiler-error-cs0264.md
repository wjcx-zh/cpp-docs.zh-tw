---
title: "編譯器錯誤 CS0264 | Microsoft Docs"
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
  - "CS0264"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0264"
ms.assetid: a8a87185-5915-4b0d-a8cd-2f129ea51b8f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0264
'type' 的部分宣告必須有相同順序的相同類型參數名稱  
  
 如果您在部分宣告中定義泛型類型，而且類型參數在所有部分宣告中的名稱或順序不一致，則會發生這個錯誤。 若要排除這個錯誤，請檢查每個部分宣告的類型參數，並確定使用參數的相同名稱和順序。 如需詳細資訊，請參閱[部分類別和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md) 和[泛型類型參數](../Topic/Generic%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0264。  
  
```  
// CS0264.cs partial class MyClass<T>  // CS0264 { } partial class MyClass <MyType> { }  
```