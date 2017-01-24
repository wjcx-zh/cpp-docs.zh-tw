---
title: "編譯器錯誤 CS0011 | Microsoft Docs"
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
  - "CS0011"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0011"
ms.assetid: 892553d7-a516-4631-84cd-94db5722c90d
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0011
無法解析類型 'type' 所參考組件 'assembly' 中的基底類別或介面 'class'  
  
 使用 **\/reference** 從檔案匯入的類別衍生自類別，或實作找不到的介面。 如果必要的 DLL 也未包含在使用 **\/reference** 的編譯中，就會發生這個狀況。  
  
 如需詳細資訊，請參閱[Add Reference Dialog Box](http://msdn.microsoft.com/zh-tw/2feb0fe2-0805-4cc9-8cba-b0315849dfb7)與[\/reference \(Import Metadata\)](../Topic/-reference%20\(C%23%20Compiler%20Options\).md)。  
  
## 範例  
  
```  
// CS0011_1.cs // compile with: /target:library public class Outer { public class B { } }  
```  
  
## 範例  
 第二個檔案會建立可定義類別 `C` 的 DLL，這個類別衍生自已在前一個範例中建立的類別 `B`。  
  
```  
// CS0011_2.cs // compile with: /target:library /reference:CS0011_1.dll // post-build command: del /f CS0011_1.dll public class C : Outer.B {}  
```  
  
## 範例  
 第三個檔案會取代第一個步驟所建立的 DLL，並省略內部類別 `B` 的定義。  
  
```  
// CS0011_3.cs // compile with: /target:library /out:cs0011_1.dll public class Outer {}  
```  
  
## 範例  
 最後，第四個檔案會參考第二個範例中定義的類別 `C`，這個類別衍生自類別 `B`，但目前遺漏該類別。  
  
 下列範例會產生 CS0011。  
  
```  
// CS0011_4.cs // compile with: /reference:CS0011_1.dll /reference:CS0011_2.dll // CS0011 expected class M { public static void Main() { C c = new C(); } }  
```  
  
## 請參閱  
 [Add Reference Dialog Box](http://msdn.microsoft.com/zh-tw/2feb0fe2-0805-4cc9-8cba-b0315849dfb7)   
 [\/reference \(Import Metadata\)](../Topic/-reference%20\(C%23%20Compiler%20Options\).md)