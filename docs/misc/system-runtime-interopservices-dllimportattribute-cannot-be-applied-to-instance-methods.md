---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; 無法套用至執行個體方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31529"
  - "bc31529"
helpviewer_keywords: 
  - "BC31529"
ms.assetid: c8bde5d7-c6bf-4d21-bb1a-e8627d65ad29
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; 無法套用至執行個體方法
非共用程序是使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 所宣告。  
  
 因為指定 .NET Framework 外部之 Unmanaged 動態連結程式庫 \(DLL\) 中所定義的取代程序，所以 Common Language Runtime \(CLR\) 可辨識這個屬性 \(attribute\) 和其 <xref:System.Runtime.InteropServices._Assembly.EntryPoint%2A> 屬性 \(property\)。 程式碼呼叫套用 <xref:System.Runtime.InteropServices.DllImportAttribute> 的程序時，Common Language Runtime 會改為呼叫指定的 Unmanaged 程序。  
  
 因為 .NET Framework 外部的 Unmanaged 平台不支援 .NET Framework 所支援的非共用程序，所以您無法使用非共用程序與它們相互溝通。  
  
 **錯誤 ID︰**BC31529  
  
### 更正這個錯誤  
  
-   如果這個程序不需要個別地套用至其類別或結構的每個執行個體，請將它宣告為 `Shared`。  
  
-   如果這個程序不能是 `Shared`，則請從這個程序的宣告中移除 <xref:System.Runtime.InteropServices.DllImportAttribute>。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Shared](../Topic/Shared%20\(Visual%20Basic\).md)