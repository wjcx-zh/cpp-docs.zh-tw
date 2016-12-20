---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; 無法套用至泛型方法，或套用至巢狀在泛型類型中的方法 | Microsoft Docs"
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
  - "vbc31526"
  - "bc31526"
helpviewer_keywords: 
  - "BC31526"
ms.assetid: 6f153808-1945-4c99-85ae-8bd3b35ee5a2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; 無法套用至泛型方法，或套用至巢狀在泛型類型中的方法
程序是使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 所宣告，但程序是泛型程序或包含在泛型類別或結構中。  
  
 因為指定 .NET Framework 外部之 Unmanaged 動態連結程式庫 \(DLL\) 中所定義的取代程序，所以 Common Language Runtime \(CLR\) 可辨識這個屬性 \(attribute\) 和其 <xref:System.Runtime.InteropServices._Assembly.EntryPoint%2A> 屬性 \(property\)。 程式碼呼叫套用 <xref:System.Runtime.InteropServices.DllImportAttribute> 的程序時，Common Language Runtime 會改為呼叫指定的 Unmanaged 程序。  
  
 因為 .NET Framework 外部的 Unmanaged 平台無法辨識泛型類型，所以您無法使用泛型類型與它們相互溝通。  
  
 **錯誤 ID︰**BC31526  
  
### 更正這個錯誤  
  
-   如果程序和其容器都不需要是泛型，則請移除 `Of` 子句，讓它們不是泛型。  
  
-   如果程序或其容器需要是泛型，則請從這個程序的宣告中移除 <xref:System.Runtime.InteropServices.DllImportAttribute>。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)