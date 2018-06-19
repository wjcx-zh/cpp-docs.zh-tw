---
title: MFC 類別建立網際網路用戶端應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, WinInet classes
- WinInet classes [MFC], classes
- classes [MFC], MFC
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
ms.assetid: 67d34117-9839-4f4b-8bb8-0e4a9471c606
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab361463a975a2a8794b3648a8f86c36e6026379
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348657"
---
# <a name="mfc-classes-for-creating-internet-client-applications"></a>建立網際網路用戶端應用程式的 MFC 類別
MFC 提供下列類別和全域函式撰寫網際網路用戶端應用程式。 縮排指出類別衍生自上面未縮排行類別。 `CGopherFile` 和`CHttpFile`衍生自`CInternetFile`，例如。 AFXINET 中宣告這些類別和全域函式。H，除了`CFileFind`，宣告於 AFX。H.  
  
## <a name="classes"></a>類別  
  
-   [CInternetSession](../mfc/reference/cinternetsession-class.md)  
  
-   [CInternetConnection](../mfc/reference/cinternetconnection-class.md)  
  
    -   [CFtpConnection](../mfc/reference/cftpconnection-class.md)  
  
    -   [CGopherConnection](../mfc/reference/cgopherconnection-class.md)  
  
    -   [CHttpConnection](../mfc/reference/chttpconnection-class.md)  
  
-   [CInternetFile](../mfc/reference/cinternetfile-class.md)  
  
    -   [CGopherFile](../mfc/reference/cgopherfile-class.md)  
  
    -   [Cinternetfile](../mfc/reference/chttpfile-class.md)  
  
-   [CFileFind](../mfc/reference/cfilefind-class.md)  
  
    -   [CFtpFileFind](../mfc/reference/cftpfilefind-class.md)  
  
    -   [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)  
  
-   [CGopherLocator](../mfc/reference/cgopherlocator-class.md)  
  
-   [CInternetException](../mfc/reference/cinternetexception-class.md)  
  
## <a name="global-functions"></a>全域函式  
  
-   [AfxParseURL](reference/internet-url-parsing-globals.md#afxparseurl)  
  
-   [AfxGetInternetHandleType](reference/internet-url-parsing-globals.md#afxgetinternethandletype)  
  
-   [AfxThrowInternetException](reference/internet-url-parsing-globals.md#afxthrowinternetexception)  
  
## <a name="see-also"></a>另請參閱  
 [Win32 網際網路擴充功能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [網際網路用戶端類別的必要條件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 類別建立網際網路用戶端應用程式](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
