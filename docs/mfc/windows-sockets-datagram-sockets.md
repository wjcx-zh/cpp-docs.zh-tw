---
title: Windows Sockets： 資料包通訊端 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sockets [MFC], datagram
- Windows Sockets [MFC], bi-directional data flow
- datagram sockets [MFC]
- Windows Sockets [MFC], datagram
- sockets [MFC], bi-directional data flow
ms.assetid: bec16a1c-74c0-4ff9-8c18-c2d87897d264
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 30ad7cab43301ae2cb7ebcb1fb4dfa850090955d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="windows-sockets-datagram-sockets"></a>Windows Sockets：資料包通訊端
本文說明兩種可用的 Windows Socket 類型之一資料包通訊端。 (另一種是[資料流通訊端](../mfc/windows-sockets-stream-sockets.md)。)  
  
 資料包通訊端支援不保證循序或不重複的雙向資料流。 資料包也不保證是可靠的。它們可能無法送達。 資料包資料可能會收到次序不對，可能會有重複的但會保留記錄資料中的界限，只要記錄都小於接收者的內部的大小限制。 您必須負責管理順序和可靠性。 （可靠性往往會有良好的區域網路 [LAN] 上的但小於等等的整個區域網路 [WAN]，例如網際網路）。  
  
 資料包是 「 無連線 」，也就是建立明確的連線。您傳送資料包訊息至指定的通訊端，您可以從指定的通訊端來接收訊息。  
  
 資料包通訊端的範例是保持系統時鐘同步處理網路的應用程式。 下列說明處理資料包通訊端中至少部分設定的額外功能： 將訊息廣播至大量的網路位址。  
  
 資料包通訊端會優於記錄導向資料流通訊端。 如需資料包通訊端的詳細資訊，請參閱 Windows Sockets 規格，可在 Windows SDK。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)   
 [Windows Sockets：背景](../mfc/windows-sockets-background.md)

