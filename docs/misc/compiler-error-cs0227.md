---
title: "編譯器錯誤 CS0227 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0227"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0227"
ms.assetid: b595a1c9-8204-4ff7-a1d0-258b0b1d6ff7
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0227
只有在編譯時指定了 \/unsafe，才會出現 unsafe 程式碼。  
  
 如果原始程式碼包含 [unsafe](../Topic/unsafe%20\(C%23%20Reference\).md) 關鍵字，則也必須使用 [\/unsafe](../Topic/-unsafe%20\(C%23%20Compiler%20Options\).md) 編譯器選項。 如需詳細資訊，請參閱[Unsafe 程式碼和指標](../Topic/Unsafe%20Code%20and%20Pointers%20\(C%23%20Programming%20Guide\).md)。  
  
 若要在 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] 中設定 unsafe 選項，請按一下主功能表中的 \[專案\]，選取 \[建置\] 窗格，然後核取 \[容許 Unsafe 程式碼\] 方塊。  
  
 下列範例會在沒有 **\/unsafe** 下編譯時產生 CS0227：  
  
```  
// CS0227.cs public class MyClass { unsafe public static void Main()   // CS0227 { } }  
```  
  
## 請參閱  
 [C\# Compiler Errors](../Topic/C%23%20Compiler%20Errors.md)