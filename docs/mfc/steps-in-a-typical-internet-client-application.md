---
title: 一般網際網路用戶端應用程式中的步驟
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], general table
- WinInet classes [MFC], programming
- Internet applications [MFC], client applications
ms.assetid: 7aba135c-7c15-4e2f-8c34-bbaf792c89a6
ms.openlocfilehash: 1e95a704a9aeabf288f76558133065806b227bcf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456195"
---
# <a name="steps-in-a-typical-internet-client-application"></a>一般網際網路用戶端應用程式中的步驟

下表顯示的步驟，您可能會執行一般的網際網路用戶端應用程式中。

|您的目標|採取的動作|效果|
|---------------|----------------------|-------------|
|開始網際網路工作階段。|建立[CInternetSession](../mfc/reference/cinternetsession-class.md)物件。|初始化 WinInet 並連接至伺服器。|
|設定網際網路查詢選項 （逾時限制或重試，範例的次數）。|使用[CInternetSession::SetOption](../mfc/reference/cinternetsession-class.md#setoption)。|如果作業成功，則傳回 FALSE。|
|建立回呼函式，來監視工作階段狀態。|使用[CInternetSession::EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback)。|建立回呼[CInternetSession::OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback)。 覆寫`OnStatusCallback`來建立您自己的回呼常式。|
|連線到網際網路伺服器、 內部網路伺服器或本機檔案。|使用[cinternetsession:: Openurl](../mfc/reference/cinternetsession-class.md#openurl)。|剖析 URL，並開啟指定伺服器的連接。 傳回[CStdioFile](../mfc/reference/cstdiofile-class.md) (如果您傳遞`OpenURL`本機檔案名稱)。 這是您用來存取伺服器或檔案從擷取的資料物件。|
|從檔案讀取。|使用[cinternetfile:: Read](../mfc/reference/cinternetfile-class.md#read)。|讀取指定使用您所提供的緩衝區的位元組數目。|
|處理例外狀況。|使用[CInternetException](../mfc/reference/cinternetexception-class.md)類別。|處理所有通用網際網路例外狀況類型。|
|結束網際網路工作階段。|處置[CInternetSession](../mfc/reference/cinternetsession-class.md)物件。|自動清除開啟檔案控制代碼和連接。|

## <a name="see-also"></a>另請參閱

[Win32 網際網路延伸模組 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[網際網路用戶端類別的必要條件](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[使用 MFC WinInet 類別建立網際網路用戶端應用程式](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
