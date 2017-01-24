---
title: "WinInet 如何讓您更輕鬆地建立網際網路用戶端應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Windows Sockets [C++], 和 WinInet 比較"
  - "WinInet 類別, 網際網路用戶端應用程式"
  - "WinInet 類別, 和 WinSock 比較"
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WinInet 如何讓您更輕鬆地建立網際網路用戶端應用程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Win32 網際網路副檔名或 WinInet，提供對一般網際網路通訊協定，包括 Gopher、FTP、HTTP。  使用 WinInet，您可以撰寫網際網路用戶端應用程式在較高的程式設計，而不必，處理 WinSock、TCP\/IP 或特定的網際網路通訊協定詳細資料。  WinInet 為所有三個通訊協定提供一致的一組函式，以熟悉的 Win32 API 介面。  這個一致性最小化需要進行的程式碼變更，則基礎通訊協定變更 \(例如，從 FTP 到 HTTP\)。  
  
 Visual C\+\+ 提供兩種方式使用 WinInet。  您可以呼叫 Win32 網際網路函式 \(直接參考在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] 的 OLE 文件以取得詳細資訊\) 也可以透過 [MFC WinInet 類別](../mfc/mfc-classes-for-creating-internet-client-applications.md)使用 WinInet。  
  
 **您可以使用 WinInet:**  
  
-   下載 HTML 網頁。  
  
     HTTP 是一種通訊協定從伺服器傳輸 HTML 網頁用戶端瀏覽器。  
  
-   傳送 FTP 要求上載或下載檔案或取得目錄的目錄。  
  
     典型的要求是下載檔案的匿名登入。  
  
-   用於網際網路存取資源使用 Gopher 的功能表系統。  
  
     功能表項目可以是幾個型別，包括其他功能表、您要搜尋的索引資料庫，新聞群組或檔案。  
  
 對於所有三個通訊協定，您建立連接，以要求至伺服器，並關閉連接。  
  
 **MFC WinInet 類別方便:**  
  
-   簡單地讀取 HTTP、FTP 和 Gopher 伺服器的資訊 \(例如讀取從硬碟檔案。  
  
-   使用 HTTP、FTP 和 Gopher 通訊協定，而不用將直接對 Winsock TCP\/IP 或。  
  
     使用 Win32 網際網路函式的開發人員不需要熟悉 TCP\/IP 或 Windows Sockets。  您可以直接仍然以通訊端層級，使用 Winsock TCP\/IP 傳輸通訊協定，不過，使用 MFC WinInet 類別存取 HTTP、FTP 和 Gopher 通訊協定跨網際網路更為容易。  對於許多常見的作業，它們使用的開發人員不需要知道特定通訊協定詳細資料。  
  
 可以在您的電腦執行做為其他電腦上的用戶端在網際網路上許多作業可能需要很長的時間。  這些作業的速度是由您的網路連線的速度通常限制，不過，它們可能受其他網路流量和作業的複雜度也會影響。  連接到遠端 FTP 伺服器，例如，要求您的電腦首先搜尋該伺服器名稱時尋找其位址。  您的應用程式會嘗試連接到伺服器在該位址。  一旦開啟連接，您的電腦與遠端伺服器將啟始與檔案傳輸通訊協定 \(FTP\) 的交談，才能實際使用連接擷取檔案之前。  
  
## 請參閱  
 [Win32 網際網路擴充功能 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [MFC 如何讓您更輕鬆地建立網際網路用戶端應用程式](../mfc/how-mfc-makes-it-easier-to-create-internet-client-applications.md)