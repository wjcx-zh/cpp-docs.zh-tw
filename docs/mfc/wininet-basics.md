---
title: WinInet 基本概念
ms.date: 11/04/2016
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
ms.openlocfilehash: b989e5c3df63ee7b5129d01468a0f869772ed286
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367329"
---
# <a name="wininet-basics"></a>WinInet 基本概念

您可以使用 WinInet 添加 FTP 支援,以便從應用程式內下載和上傳檔。 您可以覆寫[OnStatusCallback,](../mfc/reference/cinternetsession-class.md#onstatuscallback)並使用*dwContext*參數在搜尋和下載檔時向使用者提供進度資訊。

本文包含以下主題:

- [建立非常簡單的瀏覽器](#_core_create_a_very_simple_browser)

- [下載網頁](#_core_download_a_web_page)

- [FTP 檔案](#_core_ftp_a_file)

- [檢索 Gopher 目錄](#_core_retrieve_a_gopher_directory)

- [傳輸檔案時顯示進度資訊](#_core_display_progress_information_while_transferring_files)

下面的代碼摘錄演示如何創建簡單的瀏覽器、下載網頁、FTP 檔以及搜索 gopher 檔案。 它們不是作為完整示例,也不都包含異常處理。

有關 WinInet 的更多資訊,請參閱[Win32 互聯網擴展 (WinInet)。](../mfc/win32-internet-extensions-wininet.md)

## <a name="create-a-very-simple-browser"></a><a name="_core_create_a_very_simple_browser"></a>建立非常簡單的瀏覽器

[!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]

## <a name="download-a-web-page"></a><a name="_core_download_a_web_page"></a>下載網頁

[!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]

## <a name="ftp-a-file"></a><a name="_core_ftp_a_file"></a>FTP 檔案

[!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]

## <a name="retrieve-a-gopher-directory"></a><a name="_core_retrieve_a_gopher_directory"></a>檢索 Gopher 目錄

[!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]

## <a name="use-onstatuscallback"></a>使用「開啟狀態」 回退

使用 WinInet 類時,可以使用應用程式的[CInternetSession](../mfc/reference/cinternetsession-class.md)物件的[OnStatusBack](../mfc/reference/cinternetsession-class.md#onstatuscallback)成員來檢索狀態資訊。 如果派生自己的`CInternetSession`物件、重`OnStatusCallback`寫 和啟用狀態回調,MFC 將調`OnStatusCallback`用函數 ,並提供有關該 Internet 會話中所有活動的進度資訊。

因為單個工作階段可能支援多個連線(在其生存期內,這些連接可能執行許多不同的操作),`OnStatusCallback`因此需要一種機制來識別具有特定連接或事務的每個狀態更改。 該機制由 WinInet 支援類中許多成員函數提供的上下文 ID 參數提供。 這裡為**DWORD**類型,並且始終命名為*dwContext*。

分配給特定 Internet 物件的上下文僅`OnStatusCallback``CInternetSession`用於識別 物件成員中的物件引起的活動。 調用接收`OnStatusCallback`多個參數;這些參數協同工作,告訴應用程式已為哪個事務和連接取得了哪些進展。

建立物件時`CInternetSession`,可以為建構函數指定*dwContext*參數。 `CInternetSession`本身不使用上下文 ID;因此,它不使用上下文 ID。相反,它將上下文 ID 傳遞給任何**InternetConnect**派生的物件,這些物件沒有明確獲取自己的上下文 ID。 反過來,如果不顯式`CInternetConnection`指定其他上下文 ID,`CInternetFile`這些物件 將上下文 ID 傳遞給它們創建的物件。 另一方面,如果確實指定您自己的特定上下文 ID、物件及其所做的任何工作都將與該上下文 ID 相關聯。 您可以使用上下文標識標識在`OnStatusCallback`函數中為您提供的狀態資訊。

## <a name="display-progress-information-while-transferring-files"></a><a name="_core_display_progress_information_while_transferring_files"></a>傳輸檔案時顯示進度資訊

例如,如果編寫一個應用程式創建與 FTP 伺服器的連接以讀取檔,並且還連接到 HTTP 伺服器以獲取 Web`CInternetSession`頁,則您將`CInternetConnection`具有一個物件、兩`CFtpSession`個物件(`CHttpSession`一個物件, 另`CInternetFile`一個 物件是 ),以及兩個物件(每個連接一個)。 如果為*dwContext*參數使用預設值,則無法`OnStatusCallback`區分 指示 FTP 連接進度的調用和指示 HTTP 連接進度的呼叫。 如果指定*dwContext* ID,則可以稍後`OnStatusCallback`在 中 測試該 ID,您將知道生成回調的操作。

## <a name="see-also"></a>另請參閱

[MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)<br/>
[Win32 網際網路擴充功能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)
