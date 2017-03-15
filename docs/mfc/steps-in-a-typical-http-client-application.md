---
title: "一般 HTTP 用戶端應用程式中的步驟 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式 [MFC], HTTP 用戶端"
  - "用戶端應用程式 [C++], HTTP"
  - "HTTP 用戶端應用程式"
  - "網際網路應用程式 [C++], HTTP 用戶端應用程式"
  - "網際網路用戶端應用程式 [C++], HTTP 表格"
  - "WinInet 類別, HTTP"
ms.assetid: f86552e8-8acd-4b23-bdc5-0c3a247ebd74
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 一般 HTTP 用戶端應用程式中的步驟
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表顯示您在一般 HTTP 用戶端應用程式可以執行的步驟:  
  
|您的目標|您要採取的動作。|效果|  
|----------|--------------|--------|  
|啟動 HTTP 工作階段。|建立 [CInternetSession](../mfc/reference/cinternetsession-class.md) 物件。|初始化 WinInet 並連接到伺服器。|  
|連接至 HTTP 伺服器。|使用 [CInternetSession::GetHttpConnection](../Topic/CInternetSession::GetHttpConnection.md)。|傳回 [CHttpConnection](../mfc/reference/chttpconnection-class.md) 物件。|  
|開啟 HTTP 要求。|使用 [CHttpConnection::OpenRequest](../Topic/CHttpConnection::OpenRequest.md)。|傳回 [CHttpFile](../mfc/reference/chttpfile-class.md) 物件。|  
|傳送 HTTP 要求。|使用 [CHttpFile::AddRequestHeaders](../Topic/CHttpFile::AddRequestHeaders.md) 和 [CHttpFile::SendRequest](../Topic/CHttpFile::SendRequest.md)。|尋找檔案。  如果找不到檔案，則傳回 FALSE。|  
|從檔案讀取。|使用 [CHttpFile](../mfc/reference/chttpfile-class.md)。|將指定的位元組數使用您所提供的緩衝區。|  
|處理例外狀況。|使用 [CInternetException](../mfc/reference/cinternetexception-class.md) 類別。|處理所有通用網際網路例外狀況型別。|  
|結束 HTTP 工作階段。|處理 [CInternetSession](../mfc/reference/cinternetsession-class.md) 物件。|自動清除開啟檔案控制代碼和連接。|  
  
## 請參閱  
 [Win32 網際網路擴充功能 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [網際網路用戶端類別的必要條件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 類別建立網際網路用戶端應用程式](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)