---
title: "Remote Automation 使用者元件 | Microsoft Docs"
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
  - "DLL [C++], Automation"
  - "Remote Automation [C++], 使用者元件"
ms.assetid: 601591cc-a442-440a-988e-baf3284b0d46
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Remote Automation 使用者元件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您將需要確定每個用戶端包含您的用戶端程式和它需要的任何支援 DLL。  您也必須確定伺服器應用程式和它需要位於伺服器電腦的任何支援 DLL。  最後，您將需要確定您的伺服器程式在每一個用戶端註冊，在 RAC 管理員可以執行設定連接之前。  如果程式自我登錄 \(大部分都是\)，您只需要實作在用戶端的伺服器端登錄它。  如果再次失敗，您可能必須執行您提供的登錄檔案，或是手動編輯登錄。  
  
## 請參閱  
 [Automation 管理員 \(MFC\)](../mfc/automation-manager-mfc.md)   
 [Remote Automation 連接管理員](../mfc/remote-automation-connection-manager.md)   
 [Remote Automation 安裝](../mfc/remote-automation-installation.md)