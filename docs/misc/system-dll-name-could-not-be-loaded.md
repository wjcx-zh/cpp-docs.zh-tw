---
title: "System DLL &lt;name&gt; could not be loaded. | Microsoft Docs"
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
  - "vs.message.VB_E_TERRSYSDLLNOTLOADED"
  - "vs.message.0x800A0085"
ms.assetid: d4ccb3b1-fbc3-4395-a9b1-be50a4d7bf44
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# System DLL &lt;name&gt; could not be loaded.
找不到作業系統所提供的 .dll 檔案，例如 DDEML.DLL、VERSION.DLL 或 WINSPOOL.DRV。  當下列任一情形發生時，就會發生這個錯誤：檔案不在正確的路徑上、DLL 已損毀或刪除，或記憶體不足。  
  
### 若要更正這個錯誤  
  
1.  請檢查 DLL 是在 Windows\\System 路徑上。  
  
     \-或\-  
  
     重新載入 DLL。  
  
     \-或\-  
  
     嘗試關閉其他應用程式來釋放記憶體。