---
title: "編譯器錯誤 CS0171 | Microsoft Docs"
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
  - "CS0171"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0171"
ms.assetid: 8c1d76c9-1048-4579-9031-23e3566e6288
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0171
程式控制權回到呼叫端前，必須完整指派自動實作的屬性 'name' 的支援欄位。 請考慮從建構函式初始設定式中呼叫預設建構函式。  
  
 [結構](../Topic/struct%20\(C%23%20Reference\).md)中的建構函式必須初始化該結構中的所有欄位。 如需詳細資訊，請參閱[建構函式](../Topic/Constructors%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0171：  
  
```  
// CS0171.cs struct MyStruct { MyStruct(int initField)   // CS0171 { // i = initField;      // uncomment this line to resolve this error } public int i; } class MyClass { public static void Main() { MyStruct aStruct = new MyStruct(); } }  
```