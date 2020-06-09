---
title: 網際網路上的 Active 技術
ms.date: 09/12/2018
helpviewer_keywords:
- Internet applications [MFC], Active technology
ms.assetid: 6f782aa1-5c2f-47a2-9e63-ddd0829d5a08
ms.openlocfilehash: 2cd087c99c1ebdcaa8b4a44524e7691984877f20
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625145"
---
# <a name="active-technology-on-the-internet"></a>網際網路上的 Active 技術

Active 技術是一種開放平台，可讓開發人員為全域網路或為公司的內部網路 (稱為內部網路) 建立令人興奮、動態內容和應用程式。 Microsoft 針對網際網路程式設計提供的主要技術如下。

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需取代 ActiveX 之新式技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

## <a name="activex-controls"></a>ActiveX 控制項

ActiveX 控制項 (先前稱為 OLE 控制項) 是一些物件，可以插入 Web 網頁或其他 ActiveX 控制項容器的應用程式。 這些範例包含按鈕、股票行情和圖表控制項。 如需詳細資訊，請參閱[網際網路上的 ActiveX 控制項](activex-controls-on-the-internet.md)。

## <a name="internet-data-download-services"></a>網際網路資料下載服務

使用常見的通訊協定可以透過網際網路下載資料：HTTP、FTP 和 Gopher。 MFC WinInet 類別藉由抽象化 TCP/IP 和 WinSock 通訊協定，可讓您輕鬆地使用 HTTP、FTP 和 Gopher 通訊協定傳輸資料。 MFC 非同步 Moniker 類別提供一種以非同步方式，不造成封鎖下載檔案以及呈現大型物件的方式。 如需詳細資訊，請參閱[Win32 網際網路擴充功能（WinInet）](win32-internet-extensions-wininet.md)。

## <a name="active-scripts"></a>動態指令碼

VBScript 和其他的指令碼語言可連接控制項並在網頁中加入互動功能。 指令碼將處理的工作從伺服器移至用戶端。 例如，表單項目可以在用戶端進行驗證，然後再傳送到伺服器。

## <a name="html-extensions"></a>HTML 延伸模組

HTML 擴充方法 (例如物件標記) 已加入以支援控制項和指令碼。

## <a name="see-also"></a>另請參閱

[MFC 網際網路程式設計基本概念](mfc-internet-programming-basics.md)<br/>
[網際網路上的 ActiveX 控制項](activex-controls-on-the-internet.md)<br/>
[Win32 網際網路擴充功能 (WinInet)](win32-internet-extensions-wininet.md)
