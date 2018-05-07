---
title: 一般 HTTP 用戶端應用程式中的步驟 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTTP client applications [MFC]
- client applications [MFC], HTTP
- Internet applications [MFC], HTTP client applications
- applications [MFC], HTTP client
- Internet client applications [MFC], HTTP table
- WinInet classes [MFC], HTTP
ms.assetid: f86552e8-8acd-4b23-bdc5-0c3a247ebd74
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c25402662296a9ebf2f15fe902dcefabb9d47073
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="steps-in-a-typical-http-client-application"></a>一般 HTTP 用戶端應用程式中的步驟
下表顯示的步驟，您可能會執行一般的 HTTP 用戶端應用程式中：  
  
|您的目標|採取的動作|效果|  
|---------------|----------------------|-------------|  
|開始的 HTTP 工作階段。|建立[CInternetSession](../mfc/reference/cinternetsession-class.md)物件。|初始化 WinInet 並連接至伺服器。|  
|與 HTTP 伺服器的連接。|使用[CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection)。|傳回[CHttpConnection](../mfc/reference/chttpconnection-class.md)物件。|  
|開啟 HTTP 要求。|使用[chttpconnection::](../mfc/reference/chttpconnection-class.md#openrequest)。|傳回[Cinternetfile](../mfc/reference/chttpfile-class.md)物件。|  
|傳送 HTTP 要求。|使用[CHttpFile::AddRequestHeaders](../mfc/reference/chttpfile-class.md#addrequestheaders)和[CHttpFile::SendRequest](../mfc/reference/chttpfile-class.md#sendrequest)。|尋找檔案。 如果找不到檔案則傳回 FALSE。|  
|從檔案讀取。|使用[Cinternetfile](../mfc/reference/chttpfile-class.md)。|讀取指定的使用您提供的緩衝區的位元組數目。|  
|處理例外狀況。|使用[CInternetException](../mfc/reference/cinternetexception-class.md)類別。|處理所有通用網際網路例外狀況類型。|  
|結束 HTTP 工作階段。|處置[CInternetSession](../mfc/reference/cinternetsession-class.md)物件。|自動清除開啟檔案控制代碼和連接。|  
  
## <a name="see-also"></a>另請參閱  
 [Win32 網際網路擴充功能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [網際網路用戶端類別的必要條件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 類別建立網際網路用戶端應用程式](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
