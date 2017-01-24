---
title: "一般網際網路用戶端應用程式中的步驟 | Microsoft Docs"
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
  - "網際網路應用程式, 用戶端應用程式"
  - "網際網路用戶端應用程式, 一般表格"
  - "WinInet 類別, 程式設計"
ms.assetid: 7aba135c-7c15-4e2f-8c34-bbaf792c89a6
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 一般網際網路用戶端應用程式中的步驟
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表顯示您在一般網際網路用戶端應用程式可以執行的步驟。  
  
|您的目標|您要採取的動作。|效果|  
|----------|--------------|--------|  
|啟動網際網路工作階段。|建立 [CInternetSession](../mfc/reference/cinternetsession-class.md) 物件。|初始化 WinInet 並連接到伺服器。|  
|設定網際網路查詢選項 \(例如逾時重試限制或再試的數量\)。|使用 [CInternetSession::SetOption](../Topic/CInternetSession::SetOption.md)。|如果作業失敗，則傳回 FALSE。|  
|建立回呼函式監視這個工作階段的狀態。|使用 [CInternetSession::EnableStatusCallback](../Topic/CInternetSession::EnableStatusCallback.md)。|建立回呼至 [CInternetSession::OnStatusCallback](../Topic/CInternetSession::OnStatusCallback.md)。  覆寫 `OnStatusCallback` 建立您的回呼常式。|  
|連接到網際網路伺服器、內部網路伺服器或本機檔案。|使用 [CInternetSession::OpenURL](../Topic/CInternetSession::OpenURL.md)。|解析 URL 並開啟具有指定之伺服器的連接。  如果您透過 `OpenURL` 本機檔案名稱，則傳回 [CStdioFile](../mfc/reference/cstdiofile-class.md) 。  這是您從存取伺服器或檔案擷取的資料的物件。|  
|從檔案讀取。|使用 [CInternetFile::Read](../Topic/CInternetFile::Read.md)。|使用您提供的緩衝區讀取指定的位元組數。|  
|處理例外狀況。|使用 [CInternetException](../mfc/reference/cinternetexception-class.md) 類別。|處理所有通用網際網路例外狀況型別。|  
|關閉網際網路工作階段。|處理 [CInternetSession](../mfc/reference/cinternetsession-class.md) 物件。|自動清除開啟檔案控制代碼和連接。|  
  
## 請參閱  
 [Win32 網際網路擴充功能 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [網際網路用戶端類別的必要條件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 類別建立網際網路用戶端應用程式](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)