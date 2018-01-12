---
title: "MFC 資料庫應用程式檔案 功能表 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- File menu
- database applications [MFC], File menu commands
ms.assetid: 92dafb75-c1b3-4860-80a0-87a83bfc36f2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 51f630f5a3fe1ee5833ac2796ff2acb1841af4c1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="file-menu-in-an-mfc-database-application"></a>MFC 資料庫應用程式中的檔案功能表
如果您建立 MFC 資料庫應用程式，而不使用序列化，如何應該您解譯開啟、 關閉、 儲存，和將儲存為命令在 [檔案] 功能表上有此問題的樣式指南，這裡是一些建議：  
  
-   完全排除 [檔案] 功能表的 [開啟] 命令。  
  
-   解譯 [開啟] 命令為「開放式資料庫」，並為使用者顯示一份應用程式識別的資料來源清單。  
  
-   解譯 [開啟] 命令為「開啟設定檔」。 將 [開啟] 用於啟序列化檔案，但使用檔案來儲存包含「使用者設定檔」資訊的序列化文件，例如使用者的偏好設定，包括其登入 ID (可選擇不包含密碼) 和最近使用的資料來源。  
  
 MFC 應用程式精靈支援用與文件無關的 [檔案] 功能表命令建立應用程式。 選取**Database 未提供檔案支援檢視**選項**資料庫支援**頁面。  
  
 若要以特殊方式解譯 [檔案] 功能表命令，您必須覆寫一個或多個命令處理常式，多數是在您的 `CWinApp` 衍生類別中。 例如，如果您完全覆寫 `OnFileOpen` (實作 `ID_FILE_OPEN` 命令) 來表示「開啟資料庫」：  
  
-   不要呼叫 `OnFileOpen` 的基底類別版本，因為您完全取代了架構的預設命令實作。  
  
-   請改用處理常式以顯示對話方塊列示資料來源。 您可以藉由呼叫顯示一個對話方塊，這類`CDatabase::OpenEx`或`CDatabase::Open`搭配參數**NULL**。 如此會開啟顯示使用者電腦上所有可用資料來源的 ODBC 對話方塊。  
  
-   由於資料庫應用程式通常不會儲存整份文件，您可能會想要移除 [儲存] 和 [另存新檔] 實作，除非您使用序列化文件來儲存設定檔資訊。 否則，您可能會實作 [儲存] 命令，例如「認可異動」。 請參閱[技術提示 22](../mfc/tn022-standard-commands-implementation.md)如需有關覆寫這些命令。  
  
## <a name="see-also"></a>請參閱  
 [序列化︰序列化和資料庫輸入/輸出](../mfc/serialization-serialization-vs-database-input-output.md)

