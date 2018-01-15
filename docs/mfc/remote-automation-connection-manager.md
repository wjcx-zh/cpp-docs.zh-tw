---
title: "Remote Automation 連接管理員 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Automation clients [MFC], configuring for Remote Automation
- registry [MFC], remote Automation
- Automation servers [MFC], configuring for Remote Automation
- Remote Automation Connection Manager [MFC]
- Remote Automation [MFC], configuring client and server machines
- RAC Manager tool [MFC]
ms.assetid: 562eb7bc-f95c-46ad-ac97-f0dfa98362af
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cf316653b2f968fd5373c6265bb4f3f3ef3b0ba4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="remote-automation-connection-manager"></a>Remote Automation 連接管理員
若要設定用戶端和伺服器電腦，您必須變更登錄的內容。 您不需手動執行這項作業，使用 [遠端 Automation 連接 (RAC) 管理員] 工具會較為容易。 您需要將這個工具 (RACMGR32.EXE 連同 RACREG32.DLL) 複製到您所選擇的目錄。 若將此路徑放入 PATH 中，您就可以從工作列使用 [執行] 來執行該工具。 或者，您可以在 [開始] 功能表上為其建立捷徑或放置該工具的參考。  
  
 由於 RACMGR32 是 Visual Basic 撰寫，因此也需要一些支援 Visual Basic 的 DLL。 這些檔案會放置在 CD-ROM 上與 RACMGR32.EXE 相同的目錄中。 由 Visual C++ Enterprise Edition 的安裝程式安裝的這些檔案的版本與 Visual Basic Enterprise Edition 5.0 隨附的這些檔案相同或更新。 Visual C++ 安裝程式會將新版本的 Visual Basic 檔案複製到系統目錄。 若是 Windows 9x，此目錄通常會是 C:\Windows\System。 若是 Windows NT 和 Windows 2000，它通常會是 C:\WINNT\system32。 安裝程式也會向作業系統註冊這些檔案。 您可以從 Visual Basic 安裝移除它們。  
  
## <a name="see-also"></a>請參閱  
 [Automation 管理員 (MFC)](../mfc/automation-manager-mfc.md)   
 [Remote Automation 使用者元件](../mfc/remote-automation-user-components.md)   
 [Remote Automation 安裝](../mfc/remote-automation-installation.md)

