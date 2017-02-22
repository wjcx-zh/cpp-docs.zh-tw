---
title: "MFC 如何讓您更輕鬆地建立網際網路用戶端應用程式 | Microsoft Docs"
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
  - "網際網路應用程式, MFC"
  - "網際網路用戶端應用程式, MFC"
  - "MFC, 網際網路應用程式"
ms.assetid: 94437b3f-f15c-437d-b5fd-264a2efec9ab
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# MFC 如何讓您更輕鬆地建立網際網路用戶端應用程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

為 MFC 程式設計人員提供了熟悉的內容的 Microsoft Foundation Classes 封裝某些 Win32 Internet Extension \(WinInet\) 函式。  MFC 提供由 [CStdioFile](../mfc/reference/cstdiofile-class.md) 類別 \([CInternetFile](../mfc/reference/cinternetfile-class.md)、 [CHttpFile](../mfc/reference/chttpfile-class.md)和 [CGopherFile](../mfc/reference/cgopherfile-class.md)\) 衍生的三個網際網路檔案的類別。  除了這些類別進行擷取及管理網際網路資料熟悉為本機檔案使用了 `CStdioFile` 的程式設計人員，不過，與這些類別可以管理本機檔案和網際網路檔案以一致，透明模式。  
  
 MFC WinInet 類別提供跨網際網路傳輸的功能與 `CStdioFile` 相同的資料。  這些類別擷取 HTTP、FTP 和 Gopher 的網際網路通訊協定的高階 API，提供快速和直接的路徑會使應用程式網際網路感知。  例如，連接到 FTP 伺服器仍然需要幾個步驟在低，，而是為 MFC 開發人員，您只需要呼叫 `CInternetSession::GetFTPConnection` 來建立連接。  
  
 此外， MFC WinInet 類別提供下列優點:  
  
-   緩衝區的 I\/O  
  
-   資料的型別安全控制代碼  
  
-   許多函式的預設參數  
  
-   一般網際網路錯誤的例外狀況處理。  
  
-   開啟控制代碼和連接自動清除  
  
## 請參閱  
 [Win32 網際網路擴充功能 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [WinInet 如何讓您更輕鬆地建立網際網路用戶端應用程式](../mfc/how-wininet-makes-it-easier-to-create-internet-client-applications.md)