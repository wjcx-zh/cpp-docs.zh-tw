---
title: WinInet 基本概念 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 38506d0b25918bbc9d70ec1801971b070d620bf9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="wininet-basics"></a>WinInet 基本概念
您可以使用 WinInet 加入 FTP 支援下載和上傳您的應用程式中的檔案。 您可以覆寫[OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback)並用`dwContext`進度資訊提供給使用者，當您搜尋和下載檔案的參數。  
  
 本文章包含下列主題：  
  
-   [建立簡單的瀏覽器](#_core_create_a_very_simple_browser)  
  
-   [下載 Web 網頁](#_core_download_a_web_page)  
  
-   [FTP 下載檔案](#_core_ftp_a_file)  
  
-   [擷取 Gopher 目錄](#_core_retrieve_a_gopher_directory)  
  
-   [顯示進度資訊在傳輸檔案時](#_core_display_progress_information_while_transferring_files)  
  
 下面程式碼摘錄示範如何建立簡單的瀏覽器、 下載網頁上，檔案、 FTP 和 gopher 檔案搜尋。 它們不一定會做為完整的範例，而且不是全部包含例外狀況處理。  
  
 如需有關 WinInet 的詳細資訊，請參閱[Win32 網際網路擴充功能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)。  
  
##  <a name="_core_create_a_very_simple_browser"></a> 建立簡單的瀏覽器  
 [!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]  
  
##  <a name="_core_download_a_web_page"></a> 下載 Web 網頁  
 [!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]  
  
##  <a name="_core_ftp_a_file"></a> FTP 下載檔案  
 [!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]  
  
##  <a name="_core_retrieve_a_gopher_directory"></a> 擷取 Gopher 目錄  
 [!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]  
  
## <a name="use-onstatuscallback"></a>使用 OnStatusCallback  
 當使用 WinInet 類別，您可以使用[OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback)您的應用程式的成員[CInternetSession](../mfc/reference/cinternetsession-class.md)擷取狀態資訊的物件。 如果您衍生您自己`CInternetSession`物件，請覆寫`OnStatusCallback`，並啟用狀態回呼 (callback)，MFC 會呼叫您`OnStatusCallback`函式的所有活動中的網際網路工作階段的進度資訊。  
  
 因為在單一工作階段可能支援數個連線 （而超過存留期，可能會執行許多不同的作業），`OnStatusCallback`需要某種機制，找出每個狀態變更的特定連線或交易。 此機制是由內容 ID 參數提供給許多 WinInet 支援類別中的成員函式提供。 這個參數會一律屬於型別`DWORD`，一律為`dwContext`。  
  
 指派給特定的網際網路物件的內容僅用來識別該物件會導致活動`OnStatusCallback`隸屬`CInternetSession`物件。 呼叫`OnStatusCallback`接收數個參數，因此這些參數來告知您的應用程式已進行的交易與連接的哪些進度一起運作。  
  
 當您建立`CInternetSession`物件，您可以指定`dwContext`建構函式的參數。 `CInternetSession` 本身不會使用內容識別碼。相反地，它會傳遞至任何的內容識別碼**InternetConnection**-衍生不明確地取得其本身的內容識別碼的物件。 接著，這些`CInternetConnection`物件將會通過要沿著內容識別碼`CInternetFile`物件他們建立如果您未明確指定不同的內容識別碼。 如果相反地，指定您自己的特定內容識別碼、 物件和任何工作，它會將相關聯，並提供該內容識別碼。 您可以使用內容識別碼來識別哪些狀態資訊您在給定您`OnStatusCallback`函式。  
  
##  <a name="_core_display_progress_information_while_transferring_files"></a> 顯示進度資訊在傳輸檔案時  
 例如，如果您撰寫的應用程式，建立與 FTP 伺服器讀取檔案的連線，並也會連線到以取得網頁的 HTTP 伺服器，您就必須`CInternetSession`物件、 兩個`CInternetConnection`物件 (其中一個會是**CFtpSession**就是使用其他**CHttpSession**)，以及兩個`CInternetFile`物件 （一個用於每個連線）。 如果您使用預設值為`dwContext`參數，將無法區別`OnStatusCallback`指出進度的 FTP 連接和表示進行 HTTP 連接的引動過程的引動過程。 如果您指定`dwContext`識別碼，您可以稍後針對測試中`OnStatusCallback`，您就知道哪些作業會產生回呼。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)   
 [Win32 網際網路延伸模組 (WinInet)](../mfc/win32-internet-extensions-wininet.md)

