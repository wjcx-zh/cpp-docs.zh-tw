---
title: WinInet 基本概念
ms.date: 11/04/2016
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
ms.openlocfilehash: f56d2bb6e6a0b49b3d69dbcc0bf6346b72e9f7b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519180"
---
# <a name="wininet-basics"></a>WinInet 基本概念

您可以使用 WinInet 新增 FTP 支援，以下載和上傳您的應用程式中的檔案。 您可以覆寫[OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback)並用*dwContext*進度資訊提供給使用者，當您搜尋和下載檔案的參數。

這篇文章包含下列主題：

- [建立簡單的瀏覽器](#_core_create_a_very_simple_browser)

- [下載網頁](#_core_download_a_web_page)

- [FTP 檔案](#_core_ftp_a_file)

- [擷取 Gopher 目錄](#_core_retrieve_a_gopher_directory)

- [顯示進度資訊在傳輸檔案時](#_core_display_progress_information_while_transferring_files)

下列程式碼摘錄會示範如何建立簡單的瀏覽器、 下載網頁，而 ftp 下載檔案，並搜尋 gopher 檔案。 它們不一定會做為完整的範例，並不是全部包含例外狀況處理。

如需其他有關 WinInet 的詳細資訊，請參閱[Win32 網際網路擴充功能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)。

##  <a name="_core_create_a_very_simple_browser"></a> 建立簡單的瀏覽器

[!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]

##  <a name="_core_download_a_web_page"></a> 下載網頁

[!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]

##  <a name="_core_ftp_a_file"></a> FTP 檔案

[!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]

##  <a name="_core_retrieve_a_gopher_directory"></a> 擷取 Gopher 目錄

[!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]

## <a name="use-onstatuscallback"></a>使用 OnStatusCallback

WinInet 類別時，您可以使用[OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback)您的應用程式的成員[CInternetSession](../mfc/reference/cinternetsession-class.md)擷取狀態資訊的物件。 如果您衍生您自己`CInternetSession`物件，覆寫`OnStatusCallback`，並啟用狀態回呼，MFC 會呼叫您`OnStatusCallback`相關的所有活動的進度資訊，該網際網路工作階段中的函式。

因為在單一工作階段可能支援數個連結 （透過其存留期，可能會執行許多不同的作業），`OnStatusCallback`需要某種機制，識別在特定的連線或交易的每個狀態變更。 此機制是由提供給許多在 WinInet 支援類別的成員函式的內容 ID 參數提供。 此參數一律會是型別**DWORD**稱為一律*dwContext*。

指派給特定的網際網路物件的內容僅用來識別的活動物件會造成`OnStatusCallback`隸屬`CInternetSession`物件。 若要呼叫`OnStatusCallback`接收數個參數; 這些參數會共同運作來告訴您的應用程式的交易和連接已對哪些進度。

當您建立`CInternetSession`物件，您可以指定*dwContext*建構函式的參數。 `CInternetSession` 本身不會使用內容識別碼;相反地，它會傳遞到任何的內容 ID **InternetConnection**-衍生不明確地取得自己的內容識別碼的物件。 在開啟，那些`CInternetConnection`物件會傳遞要沿著內容 ID`CInternetFile`物件他們建立如果您未明確指定不同的內容識別碼。 如果相反地，您指定自己的特定內容 ID、 物件和任何工作，它會將相關聯的內容識別碼。 您可以使用內容識別碼來識別哪些狀態資訊提供給您在您`OnStatusCallback`函式。

##  <a name="_core_display_progress_information_while_transferring_files"></a> 顯示進度資訊在傳輸檔案時

例如，如果您撰寫會建立與 FTP 伺服器讀取檔案的連線，並也會連線到 HTTP 伺服器，以取得網頁上的應用程式時，您必須`CInternetSession`物件、 兩個`CInternetConnection`物件 (其中就是`CFtpSession`，其他則是`CHttpSession`)，並將兩個`CInternetFile`物件 （一個用於每個連線）。 如果您使用的預設值*dwContext*參數，就無法區別`OnStatusCallback`指出進度的 FTP 連接，並指出進度的引動過程的引動過程HTTP 連接。 如果您指定*dwContext*識別碼，您可以稍後測試在`OnStatusCallback`，您將了解哪一項作業產生的回呼。

## <a name="see-also"></a>另請參閱

[MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)<br/>
[Win32 網際網路延伸模組 (WinInet)](../mfc/win32-internet-extensions-wininet.md)

