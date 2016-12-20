---
title: "編譯器警告 (層級 1) CS0626 | Microsoft Docs"
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
  - "CS0626"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0626"
ms.assetid: 2cd5061c-80e7-48d3-8d14-be7fc642af94
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS0626
方法、運算子或存取子 'method' 已標記為外部，但其上沒有屬性。 請考慮加入 DllImport 屬性來指定外部實作  
  
 標記為 `extern` 的方法也會以屬性標記，例如 [DllImport](frlrfSystemRuntimeInteropServicesDllImportAttributeClassTopic) 屬性。  
  
 此屬性會指定實作方法的位置。 在執行階段，程式將會需要這項資訊。  
  
 下列範例會產生 CS0626：  
  
```  
// CS0626.cs // compile with: /warnaserror using System.Runtime.InteropServices; public class MyClass { static extern public void M(); // CS0626 // try the following line // [DllImport("mydll.dll")] static extern public void M(); public static void Main() { } }  
```