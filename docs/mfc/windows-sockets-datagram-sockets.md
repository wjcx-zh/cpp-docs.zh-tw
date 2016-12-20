---
title: "Windows Sockets：資料包通訊端 | Microsoft Docs"
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
  - "資料包通訊端 [C++]"
  - "通訊端 [C++], 雙向資料流程"
  - "通訊端 [C++], 資料包"
  - "Windows Sockets [C++], 雙向資料流程"
  - "Windows Sockets [C++], 資料包"
ms.assetid: bec16a1c-74c0-4ff9-8c18-c2d87897d264
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets：資料包通訊端
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明資料包通訊端，可利用兩個 Windows Sockets 的其中一種型別。\(另一個型別為 [資料流通訊端](../mfc/windows-sockets-stream-sockets.md)\)。  
  
 資料包通訊端支援不保證順序或 unduplicated 的雙向資料流。  資料包也不保證是可靠的;它們可能無法到達。  資料包資料可能會到達順序和可重複，不過，在資料的記錄界限，儲存，只要記錄小於接收器的內部大小限制。  您必須負責處理排序和可靠性。\(可靠性傾向於符合在連接網路 \[LAN\]，但是如此較少於廣域網路 \[WAN\]，例如網際網路\)。  
  
 資料包是無連接」，亦即，明確連結不會建立;您傳送資料包資訊加入至指定的通訊端，可接收從指定之通訊端的訊息。  
  
 資料包通訊端的範例是存放在網路上的系統時鐘同步處理的應用程式。  這說明資料包通訊端的其他功能在至少某些設定的:對許多網路位址的廣播訊息。  
  
 資料包通訊端和記錄導向資料的資料流通訊端好。  如需資料包通訊端的詳細資訊，請參閱 Windows Sockets 規格，在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中使用。  
  
## 請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)   
 [Windows Sockets：背景](../mfc/windows-sockets-background.md)