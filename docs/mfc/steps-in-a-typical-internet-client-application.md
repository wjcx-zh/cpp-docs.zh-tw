---
title: "一般網際網路用戶端應用程式中的步驟 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Internet client applications [MFC], general table
- WinInet classes [MFC], programming
- Internet applications [MFC], client applications
ms.assetid: 7aba135c-7c15-4e2f-8c34-bbaf792c89a6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3ce4f5b91ebd68f13510f887c65927dbe5f84133
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="steps-in-a-typical-internet-client-application"></a>一般網際網路用戶端應用程式中的步驟
下表顯示的步驟，您可能會執行一般網際網路用戶端應用程式中。  
  
|您的目標|採取的動作|效果|  
|---------------|----------------------|-------------|  
|開始網際網路工作階段。|建立[CInternetSession](../mfc/reference/cinternetsession-class.md)物件。|初始化 WinInet 並連接至伺服器。|  
|設定網際網路查詢選項 （逾時限制或重試，如範例的數目）。|使用[CInternetSession::SetOption](../mfc/reference/cinternetsession-class.md#setoption)。|如果作業成功，則傳回 FALSE。|  
|建立的回呼函式，來監視工作階段狀態。|使用[CInternetSession::EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback)。|建立回呼[CInternetSession::OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback)。 覆寫`OnStatusCallback`建立您自己的回呼常式。|  
|連線到網際網路伺服器、 內部網路伺服器或本機檔案。|使用[cinternetsession:: Openurl](../mfc/reference/cinternetsession-class.md#openurl)。|剖析 URL，並開啟連接到指定的伺服器。 傳回[Cgopherfile](../mfc/reference/cstdiofile-class.md) (如果您要傳入`OpenURL`本機檔案名稱)。 這是您用來存取伺服器或檔案從擷取的資料物件。|  
|從檔案讀取。|使用[cinternetfile:: Read](../mfc/reference/cinternetfile-class.md#read)。|讀取指定的使用您提供的緩衝區的位元組數目。|  
|處理例外狀況。|使用[CInternetException](../mfc/reference/cinternetexception-class.md)類別。|處理所有通用網際網路例外狀況類型。|  
|結束網際網路工作階段。|處置[CInternetSession](../mfc/reference/cinternetsession-class.md)物件。|自動清除開啟檔案控制代碼和連接。|  
  
## <a name="see-also"></a>請參閱  
 [Win32 網際網路擴充功能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [網際網路用戶端類別的必要條件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 類別建立網際網路用戶端應用程式](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
