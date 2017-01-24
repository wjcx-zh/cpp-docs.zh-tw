---
title: "Windows Sockets：轉換字串 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "通訊端 [C++], 多位元組字元字串轉換問題"
  - "字串轉換, 多位元組字元字串"
  - "Windows Sockets [C++], 多位元組字元字串轉換"
ms.assetid: 9df522b5-6b23-41e0-bb96-e4e623baf141
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets：轉換字串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文和兩個方針手冊說明視窗通訊端程式設計的幾個問題。  本文包含字串轉換。  其他問題的 [Windows Sockets:封鎖](../mfc/windows-sockets-blocking.md) 和 [Windows Sockets:位元組順序](../mfc/windows-sockets-byte-ordering.md)報表。  
  
 如果您從 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)類別使用或衍生自類別，您必須處理這些問題。  如果您從 [CSocket](../mfc/reference/csocket-class.md)類別使用或衍生， MFC 會為您處理它們。  
  
## 轉換字串  
 如果您 Alice 和 Bob 使用字串儲存在不同的寬字元格式，例如 Unicode 或多位元組字元集的應用程式之間 \(MBCS\)，或在其中一個和應用程式之間使用 ANSI 字串，您必須處理轉換 `CAsyncSocket`下。  使用 `CArchive` 物件與 `CSocket` 物件透過類別來管理這個 [CString](../atl-mfc-shared/reference/cstringt-class.md)的功能。  如需詳細資訊，請參閱 Windows Sockets 規格，位於 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  
  
 如需詳細資訊，請參閱：  
  
-   [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets：背景](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets：資料包通訊端](../mfc/windows-sockets-datagram-sockets.md)  
  
## 請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)