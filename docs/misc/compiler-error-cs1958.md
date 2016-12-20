---
title: "編譯器錯誤 CS1958 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1958"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1958"
ms.assetid: bb6f3bb2-ea93-4d2e-984c-da9c99f5653f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1958
物件與集合初始設定式運算式不可套用到委派建立運算式。  
  
 不像是類別或結構，委派沒有成員，因此沒有可供物件初始設定式初始化的項目。 如果您遇到這個錯誤，可能是因為委派建立運算式之後有大括號。 只要移除大括號，這個錯誤就會消失。  
  
### 更正這個錯誤  
  
1.  移除大括號。  
  
## 範例  
 下列程式碼會產生 CS1958：  
  
```  
// cs1958.cs public class MemberInitializerTest { delegate void D<T>(); public static void GenericMethod<T>() { } public static void Run() { D<int> genD = new D<int>(GenericMethod<int>) { }; // CS1958 // Try the following line instead // D<int> genD = new D<int>(GenericMethod<int>); } }  
```