---
title: "Automation 管理員 (MFC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AUTMGR32.exe"
  - "Automation 用戶端, Automation 管理員"
  - "Automation 管理員"
  - "Automation 伺服程式, Automation 管理員"
  - "Automation, Automation 管理員"
  - "Remote Automation, Automation 管理員"
ms.assetid: 6bf3429e-1946-41c5-86d0-ad7f5b8585b8
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Automation 管理員 (MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

應該將AUTMGR32.EXE複製到每一台提供遠端 Automation 物件的電腦上的Windows 系統目錄。  對於 Windows 95 和 Windows 98 ，這個目錄通常是 C:\\WINDOWS\\SYSTEM。  對於 Windows NT 和 Windows 2000 上，它通常是 C:\\WINNT\\SYSTEM32。  
  
 如果您要讓來自伺服器的回呼至用戶端，也應該複製這個可執行檔加入至每個用戶端系統目錄。  
  
 當 Automation 管理員執行時，它會顯示在伺服器電腦的小型視窗包含簡短的狀態資訊。  如果您要隱藏，請參閱 Microsoft 知識庫中的文件 Q138067。  
  
## 請參閱  
 [Remote Automation 連接管理員](../mfc/remote-automation-connection-manager.md)   
 [Remote Automation 使用者元件](../mfc/remote-automation-user-components.md)   
 [Remote Automation 安裝](../mfc/remote-automation-installation.md)