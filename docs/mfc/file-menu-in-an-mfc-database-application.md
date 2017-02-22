---
title: "MFC 資料庫應用程式中的檔案功能表 | Microsoft Docs"
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
  - "檔案功能表"
  - "資料庫應用程式 [C++], 檔案功能表命令"
ms.assetid: 92dafb75-c1b3-4860-80a0-87a83bfc36f2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# MFC 資料庫應用程式中的檔案功能表
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您建立 MFC 資料庫應用程式，而不使用序列化，您應如何解譯開啟，關閉、儲存和儲存為檔案功能表的命令?  當沒有問題時樣式指南，這幾個建議:  
  
-   完全排除檔案功能表上的開啟命令。  
  
-   說明開啟命令為「開放式資料庫」並顯示使用者應用程式識別資料來源的清單。  
  
-   說明開啟命令，或啟用，請「開啟設定檔」。保持專案開啟開啟的序列化檔案，不過，使用檔案儲存包含「使用者設定檔的資訊，例如使用者偏好的序列化的資料，包括其登入識別項 \(或者只是密碼\) 資料來源使用者最近使用。  
  
 MFC 應用程式精靈建立支援應用程式與文件相關的檔案功能表命令。  選取 **Database Support** 頁面的 **Database view without file support** 選項。  
  
 要解譯的檔案功能表命令以特殊模式，您必須覆寫一或多個命令處理常式，您主要的 `CWinApp`的衍生類別。  例如，如果您完全覆寫 \(實作 `ID_FILE_OPEN` 命令\) 的 `OnFileOpen` 表示「開啟資料庫: 」  
  
-   因為您完全取代命令的架構的預設實作，不要呼叫 `OnFileOpen`基底類別版本。  
  
-   使用處理常式顯示對話方塊資料來源。  您可以透過呼叫 `CDatabase::OpenEx` 或 `CDatabase::Open` 顯示這個對話方塊與參數 **NULL**。  如此隨即顯示在使用者電腦上的所有可用資料來源的 ODBC 對話方塊。  
  
-   由於資料庫應用程式通常不會儲存整份文件，您可能會想要移除儲存和儲存為實作，除非您使用的是序列化資料儲存設定檔資訊。  否則，您可能會實作儲存命令，例如，「執行交易」。請參閱 [Technical Note 22](../mfc/tn022-standard-commands-implementation.md) 。如需覆寫這些命令的詳細資訊。  
  
## 請參閱  
 [序列化：序列化和資料庫輸入\/輸出比較](../mfc/serialization-serialization-vs-database-input-output.md)