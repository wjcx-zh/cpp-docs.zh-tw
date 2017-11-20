---
title: "WinInet 如何讓您更輕鬆地建立網際網路用戶端應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows Sockets [MFC], vs. WinInet
- WinInet classes [MFC], vs. WinSock
- WinInet classes [MFC], Internet client applications
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cd3492afb8725ccc510d185c025a27f2ce07f7f3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="how-wininet-makes-it-easier-to-create-internet-client-applications"></a>WinInet 如何讓您更輕鬆地建立網際網路用戶端應用程式
Win32 網際網路擴充功能或 WinInet，提供一般的網際網路通訊協定，包括 gopher、 FTP 和 HTTP 存取。 使用 WinInet，您可以撰寫網際網路用戶端應用程式在更高的層級的程式設計，而不必處理 WinSock、 TCP/IP 或特定網際網路通訊協定的詳細資料。 WinInet 所有三種通訊協定，熟悉的 Win32 API 介面提供一組一致的函數。 這種一致性降到最低 （例如，從 FTP 變更為 HTTP) 會變更基礎通訊協定，進行您需要的程式碼變更。  
  
 Visual c + + 提供兩種方式，讓您可以使用 WinInet。 您可以直接呼叫 Win32 網際網路函式 （請參閱 Windows SDK，如需詳細資訊中的 OLE 文件） 或者您可以使用 WinInet 透過[MFC WinInet 類別](../mfc/mfc-classes-for-creating-internet-client-applications.md)。  
  
 **您可以使用 WinInet 至：**  
  
-   下載的 HTML 頁面。  
  
     HTTP 是用來將 HTML 網頁，從伺服器傳輸到用戶端瀏覽器的通訊協定。  
  
-   傳送 FTP 要求來上傳或下載檔案，或是取得目錄清單。  
  
     典型的要求是匿名登入以下載檔案。  
  
-   使用 gopher 的功能表系統存取網際網路上的資源。  
  
     功能表項目可以是許多類型，包括其他功能表、 一個索引的資料庫，您可以搜尋、 新聞群組或檔案。  
  
 所有的三個通訊協定，您建立連線，對伺服器提出要求，並關閉連線。  
  
 **MFC WinInet 類別可讓您輕鬆：**  
  
-   做為從硬碟機讀取檔案輕鬆地從 HTTP、 FTP 和 gopher 伺服器讀取資訊。  
  
-   使用 HTTP、 FTP 和 gopher 通訊協定，不需要直接至 WinSock 或 TCP/IP 的程式設計。  
  
     使用 Win32 網際網路函式的開發人員不需要熟悉 TCP/IP 或 Windows 通訊端。 您可以仍然在通訊端層級中，使用程式設計 WinSock 和 TCP/IP 通訊協定直接，但更容易在網際網路上使用 MFC WinInet 類別來存取 HTTP、 FTP 和 gopher 通訊協定。 許多常見的作業，開發人員不需要知道他們使用的特定通訊協定的詳細資料。  
  
 您的電腦可以做為用戶端在網際網路上的其他電腦執行的許多作業可能需要很長的時間。 這些作業的速度通常只能使用您的網路連線速度，但它們可能也會受到其他網路流量和作業的複雜度。 例如，連接到遠端 FTP 伺服器，需要您的電腦先查閱該伺服器來尋找其位址的名稱。 您的應用程式會嘗試連接到該位址的伺服器。 一旦開啟連接時，您的電腦和遠端伺服器會起始與檔案傳輸通訊協定的交談才能實際擷取檔案使用的連接。  
  
## <a name="see-also"></a>另請參閱  
 [Win32 網際網路擴充功能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [MFC 如何讓您更輕鬆地建立網際網路用戶端應用程式](../mfc/how-mfc-makes-it-easier-to-create-internet-client-applications.md)

