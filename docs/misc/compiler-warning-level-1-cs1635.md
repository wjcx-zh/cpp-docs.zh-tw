---
title: "編譯器警告 (層級 1) CS1635 | Microsoft Docs"
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
  - "CS1635"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1635"
ms.assetid: e1795880-f7ea-4dca-b15b-4ba549d7ed78
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1635
無法還原警告 'warning code'，因為它已全域停用  
  
 如果您使用 **\/nowarn** 命令列選項或專案設定來停用整個編譯單元的警告，但使用 `#pragma warning restore` 來嘗試還原該警告，則會發生這個警告。 若要解決這個錯誤，請移除 \/nowarn 命令列選項或專案設定，或移除透過命令列或專案設定所停用之任何警告的 `#pragma warning restore`。 如需詳細資訊，請參閱 [\#pragma 警告](../Topic/%23pragma%20warning%20\(C%23%20Reference\).md)主題。  
  
 下列範例會產生 CS1635：  
  
```  
// CS1635.cs // compile with: /w:1 /nowarn:162 enum MyEnum {one=1,two=2,three=3}; class MyClass { public static void Main() { #pragma warning disable 162 if (MyEnum.three == MyEnum.two) System.Console.WriteLine("Duplicate"); #pragma warning restore 162 } }  
```