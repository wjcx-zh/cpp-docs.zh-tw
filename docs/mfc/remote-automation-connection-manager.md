---
title: "Remote Automation 連接管理員 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Automation 用戶端, 為 Remote Automation 設定"
  - "Automation 伺服程式, 為 Remote Automation 設定"
  - "RAC 管理員工具"
  - "登錄, Remote Automation"
  - "Remote Automation 連接管理員"
  - "Remote Automation, 設定用戶端和伺服器電腦"
ms.assetid: 562eb7bc-f95c-46ad-ac97-f0dfa98362af
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Remote Automation 連接管理員
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要設定用戶端和伺服器電腦，您必須對登錄變更。  而非手動執行這項作業，請使用遠端自動化連接 \(RAC\) 管理員工具更為容易。  這個工具， RACMGR32.EXE，與 RACREG32.DLL 一起，需要複製到您選擇的所有目錄。  使用執行，您可以將它放在路徑，它可以從工作列執行。  或者，您可以在開始功能表可以建立捷徑加入至或將其參考。  
  
 RACMGR32 以 Visual Basic 撰寫也需要一些 Visual Basic 支援 DLL。  這些檔案會在目錄中和 RACMGR32.EXE 相同在 CD\-ROM。  由 Visual C\+\+ Enterprise Edition 的安裝程式來安裝這些檔案的版本比隨附 Visual Basic Enterprise Edition 5.0 的這些對等或最新的。  Visual C\+\+ 設定 Visual Basic 新版本檔案加入系統目錄的複本。  對於 Windows 9x，此目錄通常是 C:\\Windows\\System。  對於 Windows NT 和 Windows 2000 上，它通常是 C:\\WINNT\\system32。  設定也向作業系統的這些檔案。  您可以從 Visual Basic 安裝移除它們。  
  
## 請參閱  
 [Automation 管理員 \(MFC\)](../mfc/automation-manager-mfc.md)   
 [Remote Automation 使用者元件](../mfc/remote-automation-user-components.md)   
 [Remote Automation 安裝](../mfc/remote-automation-installation.md)