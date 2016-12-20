---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; 無法套用至介面方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31530"
  - "vbc31530"
helpviewer_keywords: 
  - "BC31530"
ms.assetid: e63f1f7d-b7df-4637-a0f4-2783479ca1af
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; 無法套用至介面方法
程序定義在介面內，但程序定義適用於 <xref:System.Runtime.InteropServices.DllImportAttribute>。  
  
 因為指定 .NET Framework 外部之 Unmanaged 動態連結程式庫 \(DLL\) 中所定義的取代程序，所以 Common Language Runtime \(CLR\) 可辨識這個屬性 \(attribute\) 和其 <xref:System.Runtime.InteropServices._Assembly.EntryPoint%2A> 屬性 \(property\)。 程式碼呼叫套用 <xref:System.Runtime.InteropServices.DllImportAttribute> 的程序時，Common Language Runtime 會改為呼叫指定的 Unmanaged 程序。  
  
 介面內的程序定義不包含任何實作，因此它無法與在 .NET Framework 外部的 Unmanaged 平台交互操作。  
  
 **錯誤 ID︰**BC31530  
  
### 更正這個錯誤  
  
-   請從此程序的定義移除 <xref:System.Runtime.InteropServices.DllImportAttribute>。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Interface Statement](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)