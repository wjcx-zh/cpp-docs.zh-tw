---
title: "一般 Gopher 用戶端應用程式中的步驟 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- WinInet classes [MFC], gopher
- Internet applications [MFC], gopher client applications
- Gopher client applications [MFC]
- Internet client applications [MFC], gopher table
ms.assetid: 3e4e1869-5da0-453d-8ba9-b648c894bb90
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5108e997336e53434ad33030c0e79be027aa4a98
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="steps-in-a-typical-gopher-client-application"></a>一般 Gopher 用戶端應用程式中的步驟
下表顯示的步驟，您可能會在一般 gopher 用戶端應用程式中執行。  
  
|您的目標|採取的動作|效果|  
|---------------|----------------------|-------------|  
|開始 gopher 的工作階段。|建立[CInternetSession](../mfc/reference/cinternetsession-class.md)物件。|初始化 WinInet 並連接至伺服器。|  
|連接至 gopher 伺服器。|使用[CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection)。|傳回[CGopherConnection](../mfc/reference/cgopherconnection-class.md)物件。|  
|Gopher 中找到的第一個資源。|使用[CGopherFileFind::FindFile](../mfc/reference/cgopherfilefind-class.md#findfile)。|尋找第一個檔案。 如果找不到檔案則傳回 FALSE。|  
|Gopher 中尋找下一個資源。|使用[CGopherFileFind::FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile)。|尋找下一個檔案。 如果找不到檔案則傳回 FALSE。|  
|開啟檔案所找到**FindFile**或`FindNextFile`進行讀取。|取得使用 gopher 定位器[CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator)。 使用[CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile)。|開啟定位器所指定的檔案。 `OpenFile`傳回[CGopherFile](../mfc/reference/cgopherfile-class.md)物件。|  
|開啟檔案，使用您提供的 gopher 定位器。|建立使用 gopher 定位器[CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator)。 使用[CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile)。|開啟定位器所指定的檔案。 `OpenFile`傳回[CGopherFile](../mfc/reference/cgopherfile-class.md)物件。|  
|從檔案讀取。|使用[CGopherFile](../mfc/reference/cgopherfile-class.md)。|讀取指定的位元組，使用您提供的緩衝區數目。|  
|處理例外狀況。|使用[CInternetException](../mfc/reference/cinternetexception-class.md)類別。|處理所有通用網際網路例外狀況類型。|  
|結束 gopher 工作階段。|處置[CInternetSession](../mfc/reference/cinternetsession-class.md)物件。|自動清除開啟檔案控制代碼和連接。|  
  
## <a name="see-also"></a>請參閱  
 [Win32 網際網路擴充功能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [網際網路用戶端類別的必要條件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 類別建立網際網路用戶端應用程式](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
