---
title: 建立網際網路用戶端應用程式的 MFC 類別
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, WinInet classes
- WinInet classes [MFC], classes
- classes [MFC], MFC
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
ms.assetid: 67d34117-9839-4f4b-8bb8-0e4a9471c606
ms.openlocfilehash: d65a2e8b373f26fe928e4c3e7c0193aec4edf2d6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618040"
---
# <a name="mfc-classes-for-creating-internet-client-applications"></a>建立網際網路用戶端應用程式的 MFC 類別

MFC 提供下列類別和全域函式來撰寫網際網路用戶端應用程式。 縮排表示類別衍生自其上方未縮排的類別。 `CGopherFile`和 `CHttpFile` 衍生自 `CInternetFile` ，例如。 這些類別和全域函式會在 AFXINET.H 中宣告。H，但 `CFileFind` 在 AFX 中宣告的除外。H.

## <a name="classes"></a>類別

- [CInternetSession](reference/cinternetsession-class.md)

- [CInternetConnection](reference/cinternetconnection-class.md)

  - [CFtpConnection](reference/cftpconnection-class.md)

  - [CGopherConnection](reference/cgopherconnection-class.md)

  - [CHttpConnection](reference/chttpconnection-class.md)

- [CInternetFile](reference/cinternetfile-class.md)

  - [CGopherFile](reference/cgopherfile-class.md)

  - [CHttpFile](reference/chttpfile-class.md)

- [CFileFind](reference/cfilefind-class.md)

  - [CFtpFileFind](reference/cftpfilefind-class.md)

  - [CGopherFileFind](reference/cgopherfilefind-class.md)

- [CGopherLocator](reference/cgopherlocator-class.md)

- [CInternetException](reference/cinternetexception-class.md)

## <a name="global-functions"></a>全域函式

- [AfxParseURL](reference/internet-url-parsing-globals.md#afxparseurl)

- [AfxGetInternetHandleType](reference/internet-url-parsing-globals.md#afxgetinternethandletype)

- [AfxThrowInternetException](reference/internet-url-parsing-globals.md#afxthrowinternetexception)

## <a name="see-also"></a>另請參閱

[Win32 網際網路擴充功能 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[網際網路用戶端類別的必要條件](prerequisites-for-internet-client-classes.md)<br/>
[使用 MFC WinInet 類別建立網際網路用戶端應用程式](writing-an-internet-client-application-using-mfc-wininet-classes.md)
