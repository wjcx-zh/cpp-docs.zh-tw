---
title: "疑難排解例外狀況：System.OutOfMemoryException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "OutOfMemoryException 類別"
ms.assetid: eb16f008-964e-40a1-91f6-6ad25fa82d5a
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.OutOfMemoryException
嘗試配置記憶體失敗時，就會擲回 <xref:System.OutOfMemoryException> 例外狀況。  
  
## 相關秘訣  
 **如果您要清除陣列，請確定它的正確大小。**  
 如需詳細資訊，Visual Basic 使用者請參閱 [陣列](../Topic/Arrays%20in%20Visual%20Basic.md)。  
  
 如需詳細資訊，C\# 使用者請參閱[陣列](../Topic/Arrays%20\(C%23%20Programming%20Guide\).md)。  
  
 **請確定您有足夠的記憶體做為內部用途及新增 Managed 物件之用。**  
 如果您正以 [!INCLUDE[Compact](../misc/includes/compact_md.md)] 方式進行程式設計，而內部用途或新增 Managed 物件所需的記憶體不足時，Common Language Runtime \(CLR\) 就會擲回這個例外狀況。 若要避免這個例外狀況，進行程式設計時請避免設計使用 64 KB 或更多記憶體的大型方法。  
  
## 備註  
 使用過多的 Managed 記憶體，通常是因為：  
  
-   將大量資料集讀入記憶體中。  
  
-   建立過多的快取項目。  
  
-   上傳或下載大型檔案。  
  
-   剖析檔案時，使用太多規則運算式 \(Regular Expression\) 或字串。  
  
-   檢視狀態過多。  
  
-   工作階段狀態中有過多資料，或工作階段過多。  
  
 在 COM 物件上叫用方法，而且這個 COM 物件會傳回包含安全陣列 \(非固定大小的陣列\) 的使用者定義型別時，便可能會擲回這個例外狀況，其中的訊息為：「存放裝置空間不足，無法完成此操作」。 這是因為 .NET Framework 無法封送處理具有安全陣列型別的結構欄位。  
  
## 請參閱  
 <xref:System.OutOfMemoryException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)