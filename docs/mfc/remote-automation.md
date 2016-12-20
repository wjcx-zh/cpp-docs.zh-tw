---
title: "Remote Automation | Microsoft Docs"
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
  - "Automation 控制程式"
  - "Automation 物件"
  - "Automation 物件, 建立"
  - "COM, Remote Automation"
  - "DCOM, Remote Automation"
  - "MFC COM, Remote Automation"
  - "MFC, COM 支援"
  - "Remote Automation"
ms.assetid: 363f87fb-08fa-4458-b089-b46365a6d4f2
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Remote Automation
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  建議 Visual C\+\+ .NET 開發人員為新的應用程式使用 DCOM 而非遠端自動化。  Visual C\+\+ .NET 不支援 Windows 95。  需要支援遠端自動化的案例在 [遠端自動化在何處適用?](../mfc/where-does-remote-automation-fit-in-q.md) 中說明。  
  
 遠端自動化是 [Automation](../mfc/automation.md) 的一種型別，其允許介面消費者可以執行位於另一部電腦的介面提供者，例如在網路上的。  
  
 本文說明如何建立可遠端叫用及執行的 Automation 物件，以及如何建立可以使用這些遠端 Automation 物件的 Automation 控制器。  它也會檢查組態選項並指出遠端自動化和 DCOM \(允許與遠端叫用及執行的自動化相關之外的介面之 COM 和 OLE 分散式版本\) 之間的主要差異。  
  
## 本章節內容  
 [DCOM \(分散式元件物件模型\) 的紀錄](../mfc/history-of-dcom.md)  
  
 [Remote Automation 適用於什麼情況？](../mfc/where-does-remote-automation-fit-in-q.md)  
  
 [Remote Automation 提供什麼功能？](../mfc/what-does-remote-automation-provide-q.md)  
  
 [Remote Automation 安全性](../mfc/security-in-remote-automation.md)  
  
 [執行緒模型](../mfc/remote-automation-threading-models.md)  
  
 [安裝](../mfc/remote-automation-installation.md)  
  
 [Automation 管理員](../mfc/automation-manager-mfc.md)  
  
-   [Remote Automation 連接管理員](../mfc/remote-automation-connection-manager.md)  
  
-   [Remote Automation 使用者元件](../mfc/remote-automation-user-components.md)  
  
 [建立使用 Remote Automation 的程式](../mfc/creating-programs-that-use-remote-automation.md)  
  
 [使用 AUTOCLIK 和 AUTODRIV 執行 Remote Automation](../mfc/running-remote-automation-using-autoclik-and-autodriv.md)  
  
## 請參閱  
 [MFC COM](../mfc/mfc-com.md)   
 [Automation](../mfc/automation.md)