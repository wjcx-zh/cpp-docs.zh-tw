---
title: "Remote Automation 使用者元件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- DLLs [MFC], Automation
- Remote Automation [MFC], user components
ms.assetid: 601591cc-a442-440a-988e-baf3284b0d46
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2f82fe529586579109434da447e26b15dcb9503a
ms.sourcegitcommit: fa7a6dccddce3747389c91277a53e296f905305c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="remote-automation-user-components"></a>Remote Automation 使用者元件
您需要確定每個用戶端電腦包含您的用戶端程式和它所需要的任何支援 DLL。 您也必須確定伺服器電腦存在伺服器應用程式和它所需的任何支援 DLL。 最後，您需要確定您的伺服器程式已在每一部用戶端電腦上註冊，才能執行 RAC 管理員以設定連接。 如果程式會進行自我登錄 (大部分都是)，您只需要在執行伺服器程式的用戶端電腦上登錄它即可。 如果登錄失敗，您可能必須執行您所提供的登錄檔案，或是手動編輯登錄。  
  
## <a name="see-also"></a>請參閱  
 [Automation 管理員 (MFC)](../mfc/automation-manager-mfc.md)   
 [Remote Automation 連接管理員](../mfc/remote-automation-connection-manager.md)   
 [Remote Automation 安裝](../mfc/remote-automation-installation.md)

