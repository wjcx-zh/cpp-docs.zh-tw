---
title: 一般 Gopher 用戶端應用程式中的步驟
ms.date: 11/04/2016
helpviewer_keywords:
- WinInet classes [MFC], gopher
- Internet applications [MFC], gopher client applications
- Gopher client applications [MFC]
- Internet client applications [MFC], gopher table
ms.assetid: 3e4e1869-5da0-453d-8ba9-b648c894bb90
ms.openlocfilehash: 123b8abd2ca65356c584fa52f9415504bcb701c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486420"
---
# <a name="steps-in-a-typical-gopher-client-application"></a>一般 Gopher 用戶端應用程式中的步驟

下表顯示的步驟，您可能會執行一般 gopher 用戶端應用程式中。

|您的目標|採取的動作|效果|
|---------------|----------------------|-------------|
|開始 gopher 工作階段。|建立[CInternetSession](../mfc/reference/cinternetsession-class.md)物件。|初始化 WinInet 並連接至伺服器。|
|連接至 gopher 伺服器。|使用[Getgopherconnection](../mfc/reference/cinternetsession-class.md#getgopherconnection)。|傳回[CGopherConnection](../mfc/reference/cgopherconnection-class.md)物件。|
|Gopher 中找到的第一個資源。|使用[CGopherFileFind::FindFile](../mfc/reference/cgopherfilefind-class.md#findfile)。|尋找第一個檔案。 如果找不到檔案則傳回 FALSE。|
|Gopher 中尋找下一個資源。|使用[CGopherFileFind::FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile)。|尋找下一個檔案。 如果找不到檔案則傳回 FALSE。|
|開啟所找到的檔案`FindFile`或`FindNextFile`進行讀取。|取得使用 gopher 定位器[CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator)。 使用[CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile)。|會開啟尋找程式所指定的檔案。 `OpenFile` 會傳回[CGopherFile](../mfc/reference/cgopherfile-class.md)物件。|
|開啟檔案，使用您提供 gopher 定位器。|建立使用 gopher 定位器[CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator)。 使用[CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile)。|會開啟尋找程式所指定的檔案。 `OpenFile` 會傳回[CGopherFile](../mfc/reference/cgopherfile-class.md)物件。|
|從檔案讀取。|使用[CGopherFile](../mfc/reference/cgopherfile-class.md)。|讀取指定的位元組，使用您所提供的緩衝區數目。|
|處理例外狀況。|使用[CInternetException](../mfc/reference/cinternetexception-class.md)類別。|處理所有通用網際網路例外狀況類型。|
|結束 gopher 工作階段。|處置[CInternetSession](../mfc/reference/cinternetsession-class.md)物件。|自動清除開啟檔案控制代碼和連接。|

## <a name="see-also"></a>另請參閱

[Win32 網際網路延伸模組 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[網際網路用戶端類別的必要條件](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[使用 MFC WinInet 類別建立網際網路用戶端應用程式](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
