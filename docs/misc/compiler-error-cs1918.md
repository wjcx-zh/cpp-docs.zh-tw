---
title: "編譯器錯誤 CS1918 | Microsoft Docs"
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
  - "CS1918"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1918"
ms.assetid: 9ad2cbbd-3c10-4d56-b4cd-385103d005d4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1918
類型 'type' 且屬性為 'name' 的成員，無法以物件初始設定式進行指派，因為其為實值類型。  
  
 如果您嘗試使用物件初始設定式所初始化的結構類型屬性，本身就是所初始化類別的屬性，會發生這個錯誤。  
  
### 更正這個錯誤  
  
1.  如果您必須完整初始化物件初始設定式中屬性的欄位，請將結構變更為類別類型。 否則，請在使用物件初始設定式建立物件之後，於不同的方法呼叫中初始化結構成員。  
  
## 範例  
 下列範例會產生 CS1918：  
  
```  
// cs1918.cs public struct MyStruct { public int i; } public class Test { private MyStruct str = new MyStruct(); public MyStruct Str { get { return str; } } public static int Main() { Test t = new Test { Str = { i = 1 } }; // CS1918 return 0; } }  
  
```  
  
## 請參閱  
 [物件和集合初始設定式](../Topic/Object%20and%20Collection%20Initializers%20\(C%23%20Programming%20Guide\).md)