---
title: "編譯器錯誤 CS1613 | Microsoft Docs"
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
  - "CS1613"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1613"
ms.assetid: 9d7ea9c8-9953-459f-a3f0-c7e65d1b9f59
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1613
找不到介面 'interface' 的 Managed coclass 包裝函式類別 'class' \(是否遺漏了組件參考？\)  
  
 嘗試透過介面具現化 COM 物件。 這個介面具有 **ComImport** 和 `CoClass` 屬性，但是編譯器找不到指定給 `CoClass` 屬性的類型。  
  
 若要解決這個錯誤，您可以嘗試下列其中一種方式：  
  
-   加入具有 coclass 之組件的參考 \(介面和 coclass 大部分的時間都應該在相同的組件中\)。 如需相關資訊，請參閱 [\/reference](../Topic/-reference%20\(C%23%20Compiler%20Options\).md) 或[加入參考對話方塊](http://msdn.microsoft.com/zh-tw/2feb0fe2-0805-4cc9-8cba-b0315849dfb7)。  
  
-   修正介面上的 `CoClass` 屬性。  
  
 下列範例示範 **CoClassAttribute** 的正確用法：  
  
```  
// CS1613.cs using System; using System.Runtime.InteropServices; [Guid("1FFD7840-E82D-4268-875C-80A160C23296")] [ComImport()] [CoClass(typeof(A))] public interface IA{} public class A : IA {} public class AA { public static void Main() { IA i; i = new IA(); // This is equivalent to new A(). // because of the CoClass attribute on IA } }  
```