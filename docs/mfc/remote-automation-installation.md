---
title: "Remote Automation 安裝 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Remote Automation [MFC], installation
- installing Remote Automation [MFC]
ms.assetid: 9a02c9f6-dfc6-4489-b240-a1afe25fa0c5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: acd8ee55261dfa03c68aef506dc90188d8d27d37
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="remote-automation-installation"></a>Remote Automation 安裝
Remote Automation 有相對較少的元件：  
  
-   Remote Automation 用戶端 proxy，AUTPRX32。DLL。  
  
-   Remote Automation 伺服器端元件，Automation 管理員，AUTMGR32。EXE。  
  
-   RAC 管理員，由於 RACMGR32。與它相符 RACREG32 EXE。DLL。  
  
 其中，RAC 管理員以 Visual Basic 撰寫，因此需要 Visual Basic 執行階段支援。 這些和其他 Remote Automation 檔案會安裝安裝程式時安裝 Visual c + + Enterprise Edition。  
  
 如果您將 Remote Automation 元件複製到電腦未安裝 Enterprise Edition 的 Visual c + + 版本，請確定該 REGSRV32。EXE 所在電腦的路徑，並註冊 RACREG32。使用下列命令列的 DLL:  
  
 REGSRVR32 RACREG32。DLL  
  
> [!NOTE]
>  需要 GUAGE32 版本的 RAC 管理員之前 Visual c + + 5.0。OCX 和 TABCTL32。OCX。 這兩種情況都需要 RAC 管理員版本隨附的 Visual c + + Enterprise Edition 5.0 或更新版本。  
  
## <a name="in-this-section"></a>本節內容  
 [Automation 管理員](../mfc/automation-manager-mfc.md)  
  
 [Remote Automation 連接管理員](../mfc/remote-automation-connection-manager.md)  
  
 [Remote Automation 使用者元件](../mfc/remote-automation-user-components.md)  
  
## <a name="see-also"></a>請參閱  
 [Remote Automation](../mfc/remote-automation.md)

