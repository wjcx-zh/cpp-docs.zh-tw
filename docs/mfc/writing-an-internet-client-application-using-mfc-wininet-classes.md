---
title: "使用 MFC WinInet 類別建立網際網路用戶端應用程式 | Microsoft Docs"
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
  - "網際網路應用程式, 用戶端應用程式"
  - "網際網路應用程式, WinInet"
  - "網際網路用戶端應用程式"
  - "網際網路用戶端應用程式, 撰寫"
  - "MFC, 網際網路應用程式"
  - "WinInet 類別, 程式設計"
ms.assetid: a2c4a40c-a94e-4b3e-9dbf-f8a8dc8e5428
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 MFC WinInet 類別建立網際網路用戶端應用程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每個網際網路用戶端應用程式的基礎是網際網路工作階段。  MFC 實作網際網路工作階段為 [CInternetSession](../mfc/reference/cinternetsession-class.md) 類別的物件。  使用這個類別，您可以建立一個網際網路工作階段或多個同時執行的工作階段。  
  
 要與伺服器通訊，您需要 [CInternetConnection](../mfc/reference/cinternetconnection-class.md) 物件以及 `CInternetSession`。  您可以使用 [CInternetSession::GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md)、 [CInternetSession::GetHttpConnection](../Topic/CInternetSession::GetHttpConnection.md)或 [CInternetSession::GetGopherConnection](../Topic/CInternetSession::GetGopherConnection.md)，建立 `CInternetConnection` 。  這些呼叫對應於每個專用的通訊協定類型。  這些呼叫不會在伺服器上開啟檔案作讀取或寫入。  如果您要讀取或寫入資料，您必須在不同的步驟開啟檔案。  
  
 對於大部分的網際網路工作階段， `CInternetSession` 物件與 [CInternetFile](../mfc/reference/cinternetfile-class.md) 物件共同工作:  
  
-   對於網際網路工作階段，您必須建立 [CInternetSession](../mfc/reference/cinternetsession-class.md) 執行個體。  
  
-   如果您的網際網路工作階段讀取或寫入資料，您必須建立 `CInternetFile` 執行個體 \(或其子類別， [CHttpFile](../mfc/reference/chttpfile-class.md) 或 [CGopherFile](../mfc/reference/cgopherfile-class.md)\)。  讀取資料的最簡單的方法是呼叫 [CInternetSession::OpenURL](../Topic/CInternetSession::OpenURL.md)。  這個函式解析您提供的 Universal Resource Locator \(URL\)，由指定的 URL 開啟與伺服器的連接，並傳回唯讀的 `CInternetFile` 物件。  `CInternetSession::OpenURL` 未特定於任一通訊協定類型— 相同的呼叫可以於 FTP、HTTP 或 gopher URL 執行。  `CInternetSession::OpenURL` 甚至可與本機檔案一起使用 \(傳回 `CStdioFile` 而非 `CInternetFile`\)。  
  
-   如果您的網際網路工作階段沒有讀取或寫入資料，不過在 FTP 目錄執行其他工作，例如刪除檔案，您可能不需要建立 `CInternetFile`的執行個體。  
  
 有兩種方法可以建立 `CInternetFile` 物件：  
  
-   如果您使用 `CInternetSession::OpenURL` 建立您的伺服器連接，對 `OpenURL` 的呼叫傳回 `CStdioFile`。  
  
-   如果使用 **CInternetSession::GetFtpConnection**、 `GetGopherConnection`或 `GetHttpConnection` 建立您的伺服器連接，您必須個別呼叫 `CFtpConnection::OpenFile`、 `CGopherConnection::OpenFile`或 **CHttpConnection::OpenRequest,** ，分別傳回 `CInternetFile`、 `CGopherFile`或 `CHttpFile`。  
  
 在實作網際網路用戶端應用程式的步驟依據您是否會跟據 **OpenURL**  建立泛型網際網路用戶端或使用其中一個 **GetConnection** 函式建立通訊協定特定用戶端而定。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [如何撰寫主要與 FTP、HTTP 和 Gopher 一起使用的網際網路用戶端應用程式?](../mfc/steps-in-a-typical-internet-client-application.md)  
  
-   [如何撰寫用以開啟檔案的 FTP 用戶端應用程式?](../mfc/steps-in-a-typical-ftp-client-application.md)  
  
-   [如何撰寫不開啟檔案，但是執行目錄作業，例如刪除檔案的 FTP 用戶端應用程式?](../mfc/steps-in-a-typical-ftp-client-application-to-delete-a-file.md)  
  
-   [如何撰寫 Gopher 用戶端應用程式?](../mfc/steps-in-a-typical-gopher-client-application.md)  
  
-   [如何撰寫 HTTP 用戶端應用程式?](../mfc/steps-in-a-typical-http-client-application.md)  
  
## 請參閱  
 [Win32 網際網路擴充功能 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [建立網際網路用戶端應用程式的 MFC 類別](../mfc/mfc-classes-for-creating-internet-client-applications.md)   
 [網際網路用戶端類別的必要條件](../mfc/prerequisites-for-internet-client-classes.md)