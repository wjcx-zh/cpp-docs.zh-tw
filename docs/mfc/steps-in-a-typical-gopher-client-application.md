---
title: "一般 Gopher 用戶端應用程式中的步驟 | Microsoft Docs"
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
  - "Gopher 用戶端應用程式"
  - "網際網路應用程式, gopher 用戶端應用程式"
  - "網際網路用戶端應用程式, gopher 資料表"
  - "WinInet 類別, gopher"
ms.assetid: 3e4e1869-5da0-453d-8ba9-b648c894bb90
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 一般 Gopher 用戶端應用程式中的步驟
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表顯示您在一般 Gopher 用戶端應用程式可以執行的步驟。  
  
|您的目標|您採取的動作|效果|  
|----------|------------|--------|  
|啟動 Gopher 工作階段。|建立 [CInternetSession](../mfc/reference/cinternetsession-class.md) 物件。|初始化 WinInet 並連接到伺服器。|  
|連接 Gopher 伺服器。|使用 [CInternetSession::GetGopherConnection](../Topic/CInternetSession::GetGopherConnection.md)。|傳回 [CGopherConnection](../mfc/reference/cgopherconnection-class.md) 物件。|  
|尋找 Gopher 中的第一個資源。|使用 [CGopherFileFind::FindFile](../Topic/CGopherFileFind::FindFile.md)。|尋找第一個檔案。  如果找不到檔案則回傳 false。|  
|尋找 Gopher 中的下一個資源。|使用 [CGopherFileFind::FindNextFile](../Topic/CGopherFileFind::FindNextFile.md)。|尋找下一個檔案。  如果找不到檔案，則傳回 FALSE。|  
|使用 **FindFile** 或 `FindNextFile` 開啟找到的檔案，以便讀取。|使用 [CGopherFileFind::GetLocator](../Topic/CGopherFileFind::GetLocator.md)，取得 Gopher 定位器。  使用 [CGopherConnection::OpenFile](../Topic/CGopherConnection::OpenFile.md)。|開啟定位器指定的檔案。  `OpenFile` 會傳回 [CGopherFile](../mfc/reference/cgopherfile-class.md) 物件。|  
|使用您所提供的 Gopher 定位器開啟檔案。|使用 [CGopherConnection::CreateLocator](../Topic/CGopherConnection::CreateLocator.md)，建立 Gopher 定位器。  使用 [CGopherConnection::OpenFile](../Topic/CGopherConnection::OpenFile.md)。|開啟定位器指定的檔案。  `OpenFile` 會傳回 [CGopherFile](../mfc/reference/cgopherfile-class.md) 物件。|  
|從檔案讀取。|使用 [CGopherFile](../mfc/reference/cgopherfile-class.md)。|使用您提供的緩衝區讀取指定的位元組數。|  
|處理例外狀況。|使用 [CInternetException](../mfc/reference/cinternetexception-class.md) 類別。|處理所有通用網際網路例外狀況型別。|  
|結束 Gopher 工作階段。|處理 [CInternetSession](../mfc/reference/cinternetsession-class.md) 物件。|自動清除開啟檔案控制代碼和連接。|  
  
## 請參閱  
 [Win32 網際網路擴充功能 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [網際網路用戶端類別的必要條件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 類別建立網際網路用戶端應用程式](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)