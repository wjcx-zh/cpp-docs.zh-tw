---
title: "Remote Automation 安裝 | Microsoft Docs"
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
  - "安裝 Remote Automation"
  - "Remote Automation, 安裝"
ms.assetid: 9a02c9f6-dfc6-4489-b240-a1afe25fa0c5
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Remote Automation 安裝
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

遠端自動化有少數元件:  
  
-   遠端 Automation 用戶端 Proxy， AUTPRX32.DLL。  
  
-   遠端 Automation 伺服器端元件， Automation 管理員， AUTMGR32.EXE。  
  
-   RAC 管理員， RACMGR32.EXE，與其相符的 RACREG32.DLL。  
  
 其中， RAC 管理員以 Visual Basic 撰寫也需要 Visual Basic 執行階段支援。  安裝套件時， Visual C\+\+ Enterprise Edition 時，這些屬性和其他遠端自動化檔案由設定安裝。  
  
 如果您複製遠端 Automation 元件加入至 Visual C\+\+ 版本企業版未安裝的電腦上，請確定 REGSRV32.EXE 電腦上的路徑使用下列命令列，並註冊 RACREG32.DLL:  
  
 REGSRVR32 RACREG32.DLL  
  
> [!NOTE]
>  RAC 管理員版本 Visual C\+\+ 5.0 之前的要求 GUAGE32.OCX 和 TABCTL32.OCX。  兩者皆不是這些不需要有的 RAC 管理員版本隨附於 Visual C\+\+ Enterprise Edition，版本 5.0 \(含\) 以後版本是必要的。  
  
## 本章節內容  
 [Automation 管理員](../mfc/automation-manager-mfc.md)  
  
 [Remote Automation 連接管理員](../mfc/remote-automation-connection-manager.md)  
  
 [Remote Automation 使用者元件](../mfc/remote-automation-user-components.md)  
  
## 請參閱  
 [Remote Automation](../mfc/remote-automation.md)