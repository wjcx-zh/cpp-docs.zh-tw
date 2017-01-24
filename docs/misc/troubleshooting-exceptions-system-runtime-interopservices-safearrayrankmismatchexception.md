---
title: "疑難排解例外狀況：System.Runtime.InteropServices.SafeArrayRankMismatchException | Microsoft Docs"
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
  - "EHSafeArrayRankMismatch"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "SafeArrayRankMismatchException 類別"
ms.assetid: 6c69355c-8bfd-49bb-acad-b4d7236ae2e7
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Runtime.InteropServices.SafeArrayRankMismatchException
當收到的 SAFEARRAY 陣序不符合 Managed 簽章中指定的陣序時，就會擲回 <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> 例外狀況。  
  
## 相關秘訣  
 **請確定陣列擁有所需的維度數目。**  
 因為無法從型別程式庫來判斷安全陣列的陣序和界限，所以陣序會假設等於 1，而下限假設等於 0。 陣序和界限必須在[Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md) 所產生的 Managed 簽章中定義。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [陣列的預設封送處理](../Topic/Default%20Marshaling%20for%20Arrays.md)   
 [陣列](../Topic/Arrays%20in%20Visual%20Basic.md)