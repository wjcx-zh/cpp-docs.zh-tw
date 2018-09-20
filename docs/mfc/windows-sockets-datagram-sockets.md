---
title: Windows Sockets： 資料包通訊端 |Microsoft Docs
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
ms.openlocfilehash: 7a63caa786ce5198fb902b8d48101507fb2b4113
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444209"
---
# <a name="windows-sockets-datagram-sockets"></a>Windows Sockets：資料包通訊端

本文說明資料包通訊端，其中一個可用的兩個 Windows 通訊端類型。 (另一個型別是[資料流通訊端](../mfc/windows-sockets-stream-sockets.md)。)

資料包通訊端支援不保證循序或不重複的雙向資料流。 資料包也不保證能夠穩定可靠;它們可能會失敗，才會送達。 資料包資料可能會抵達順序，可能會有重複的但保留記錄資料中的界限，只要記錄都小於收件者內部的大小限制。 您必須負責管理排序與可靠性。 （可靠性通常是在區域網路 [LAN] 上很好的但較不等的整個區域網路 [WAN]，例如網際網路）。

資料包是 「 無 」，也就是建立明確的連線;您傳送的資料包訊息至指定的通訊端，您可以從指定的通訊端接收訊息。

資料包通訊端的範例是保持系統時鐘同步處理在網路的應用程式。 這說明了在至少部分設定的資料包通訊端的另一項功能： 將訊息廣播到大量的網路位址。

資料包通訊端會優於記錄導向資料流通訊端。 如需資料包通訊端的詳細資訊，請參閱 Windows Sockets 規格，可在 Windows SDK。

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)<br/>
[Windows Sockets：背景](../mfc/windows-sockets-background.md)

