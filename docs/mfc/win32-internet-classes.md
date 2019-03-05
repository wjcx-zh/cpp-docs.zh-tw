---
title: Win32 網際網路類別
ms.date: 09/12/2018
f1_keywords:
- vc.classes.win32
helpviewer_keywords:
- Internet classes [MFC]
- WinInet classes [MFC], classes
- Win32 [MFC], Internet classes
- Windows API [MFC], Internet classes
ms.assetid: b49601d5-3025-4068-9408-316b54ee4375
ms.openlocfilehash: c067d0c0067ee13b0e6ce6d84fd97135274c88b5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260552"
---
# <a name="win32-internet-classes"></a>Win32 網際網路類別

MFC 包裝 Win32 Internet (WinInet) 和 ActiveX 技術，以便於網際網路程式設計。

>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需有關取代 ActiveX 的現代技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

[CInternetSession](../mfc/reference/cinternetsession-class.md)<br/>
建立和初始化一個網際網路工作階段或數個同時網際網路工作階段，如有必要，將告訴您連線到 proxy 伺服器。

[CInternetConnection](../mfc/reference/cinternetconnection-class.md)<br/>
管理您與網際網路伺服器的連接。

[CInternetFile](../mfc/reference/cinternetfile-class.md)<br/>
此類別和其衍生的類別允許在使用網際網路通訊協定的遠端系統上的檔案的存取權。

[CHttpConnection](../mfc/reference/chttpconnection-class.md)<br/>
管理您與 HTTP 伺服器的連接。

[CHttpFile](../mfc/reference/chttpfile-class.md)<br/>
提供的功能來尋找和讀取 HTTP 伺服器上的檔案。

[CGopherFile](../mfc/reference/cgopherfile-class.md)<br/>
提供在 Gopher 伺服器上尋找和讀取檔案的功能。

[CFtpConnection](../mfc/reference/cftpconnection-class.md)<br/>
管理您連接到 FTP 伺服器。

[CGopherConnection](../mfc/reference/cgopherconnection-class.md)<br/>
管理您連接至 gopher 伺服器。

[CFileFind](../mfc/reference/cfilefind-class.md)<br/>
執行本機和網際網路檔案搜尋。

[CFtpFileFind](../mfc/reference/cftpfilefind-class.md)<br/>
協助 FTP 伺服器的網際網路檔案搜尋。

[CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)<br/>
協助網際網路檔案搜尋 Gopher 伺服器。

[CGopherLocator](../mfc/reference/cgopherlocator-class.md)<br/>
從 Gopher 伺服器取得 Gopher「定位器」，判斷定位器的類型，並將定位器提供給 `CGopherFileFind`。

[CInternetException](../mfc/reference/cinternetexception-class.md)<br/>
表示與網際網路作業相關的例外狀況。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)
