---
title: 使用 MFC WinInet 類別建立網際網路用戶端應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet client applications [MFC]
- WinInet classes [MFC], programming
- Internet client applications [MFC], writing
- Internet applications [MFC], WinInet
- Internet applications [MFC], client applications
- MFC, Internet applications
ms.assetid: a2c4a40c-a94e-4b3e-9dbf-f8a8dc8e5428
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 00ace36eef483d8385d718e14e1fc4c5f4e9ea1e
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956467"
---
# <a name="writing-an-internet-client-application-using-mfc-wininet-classes"></a>使用 MFC WinInet 類別建立網際網路用戶端應用程式
所有網際網路用戶端應用程式的基礎都是網際網路工作階段。 MFC 網際網路工作階段實作為類別的物件[CInternetSession](../mfc/reference/cinternetsession-class.md)。 使用這個類別，您就可以建立一個網際網路工作階段或多個同時執行的工作階段。  
  
 若要與伺服器通訊，您需要[CInternetConnection](../mfc/reference/cinternetconnection-class.md)物件以及`CInternetSession`。 您可以建立`CInternetConnection`使用[cinternetsession:: Getftpconnection](../mfc/reference/cinternetsession-class.md#getftpconnection)， [CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection)，或[CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection). 這些呼叫都是專屬的通訊協定類型。 這些呼叫不會在伺服器上開啟檔案進行讀取或寫入。 如果要讀取或寫入資料，您必須透過不同的步驟開啟檔案。  
  
 對於大部分的網際網路工作階段，`CInternetSession`物件可手中-緊密與[CInternetFile](../mfc/reference/cinternetfile-class.md)物件：  
  
-   對於網際網路工作階段中，您必須建立的執行個體[CInternetSession](../mfc/reference/cinternetsession-class.md)。  
  
-   如果您的網際網路工作階段中讀取或寫入資料，您必須建立的執行個體`CInternetFile`(或其子類別[Cinternetfile](../mfc/reference/chttpfile-class.md)或[CGopherFile](../mfc/reference/cgopherfile-class.md))。 讀取資料最簡單的方式是呼叫[cinternetsession:: Openurl](../mfc/reference/cinternetsession-class.md#openurl)。 這個函式會解析您所提供的統一資源定位器 (URL)，開啟與以 URL 指定的伺服器連接，並傳回唯讀的 `CInternetFile` 物件。 `CInternetSession::OpenURL` 未專屬於任一通訊協定類型，相同的呼叫可以於 FTP、HTTP 或 gopher URL 上執行。 `CInternetSession::OpenURL` 甚至可搭配本機檔案一起使用 (會傳回 `CStdioFile` 而非 `CInternetFile`)。  
  
-   如果您的網際網路工作階段沒有讀取或寫入資料，但會執行其他工作 (例如在 FTP 目錄中刪除檔案)，則您可能不需要建立 `CInternetFile` 的執行個體。  
  
 建立 `CInternetFile` 物件的方法有兩種：  
  
-   如果您使用 `CInternetSession::OpenURL` 建立您的伺服器連接，則呼叫 `OpenURL` 會傳回 `CStdioFile`。  
  
-   如果使用`CInternetSession::GetFtpConnection`， `GetGopherConnection`，或`GetHttpConnection`建立伺服器連接，您必須呼叫`CFtpConnection::OpenFile`， `CGopherConnection::OpenFile`，或`CHttpConnection::OpenRequest`，分別傳回`CInternetFile`， `CGopherFile`，或`CHttpFile`，分別。  
  
 根據您要建立根據一般網際網路用戶端實作網際網路用戶端應用程式中的步驟而有所不同`OpenURL`或使用其中一種通訊協定特定用戶端`GetConnection`函式。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [如何撰寫一般會搭配 FTP、 HTTP 和 gopher 的網際網路用戶端應用程式](../mfc/steps-in-a-typical-internet-client-application.md)  
  
-   [如何撰寫用以開啟檔案的 FTP 用戶端應用程式](../mfc/steps-in-a-typical-ftp-client-application.md)  
  
-   [如何撰寫不開啟檔案，但執行目錄作業，例如刪除檔案的 FTP 用戶端應用程式](../mfc/steps-in-a-typical-ftp-client-application-to-delete-a-file.md)  
  
-   [如何撰寫 gopher 用戶端應用程式](../mfc/steps-in-a-typical-gopher-client-application.md)  
  
-   [如何撰寫 HTTP 用戶端應用程式](../mfc/steps-in-a-typical-http-client-application.md)  
  
## <a name="see-also"></a>另請參閱  
 [Win32 網際網路擴充功能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [建立網際網路用戶端應用程式的 MFC 類別](../mfc/mfc-classes-for-creating-internet-client-applications.md)   
 [網際網路用戶端類別的必要條件](../mfc/prerequisites-for-internet-client-classes.md)
