---
title: "疑難排解例外狀況：System.AccessViolationException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.AccessViolationException 例外狀況"
  - "AccessViolationException 類別"
ms.assetid: 7f09315d-8aad-4ab1-8b5e-21a8c97f6c14
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.AccessViolationException
嘗試讀取或寫入受保護的記憶體時，就會擲回 <xref:System.AccessViolationException>。  
  
## 相關秘訣  
 請確定已配置您嘗試存取的記憶體。  
 自動記憶體管理是 Common Language Runtime \(CLR\) 提供的一項服務。 您可能會希望移動到 Managed 程式碼，以便利用這項服務。 如需詳細資訊，請參閱[自動記憶體管理](../Topic/Automatic%20Memory%20Management.md)。  
  
 請確定您嘗試存取的記憶體並未損毀。  
 如果透過損壞的指標進行數次讀取或寫入作業，可能會損毀記憶體。  
  
### 備註  
 嘗試讀取或寫入未經配置或沒有存取權的記憶體時，Unmanaged 或 Unsafe 程式碼會發生存取違規。 並非所有透過錯誤指標讀取或寫入的動作都會導致存取違規，因此存取違規通常指出已透過錯誤指標執行多次讀取或寫入，且該記憶體可能已毀損。  
  
 在 Managed 程式碼中，所有參考不是有效的就是 null。 嘗試在可驗證程式碼中參考 null 參考的任何作業，都會擲回 <xref:System.NullReferenceException>。  
  
 在 Unsafe Managed 程式碼中發生的存取違規，可能會以 <xref:System.NullReferenceException> 或 <xref:System.AccessViolationException> 說明 \(依平台而定\)。  
  
 反昇至 Managed 程式碼的 Unmanaged 程式碼存取違規，一律會包覆在 <xref:System.AccessViolationException> 中。  
  
## 請參閱  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [記憶體管理：範例](../mfc/memory-management-examples.md)   
 [自動記憶體管理](../Topic/Automatic%20Memory%20Management.md)