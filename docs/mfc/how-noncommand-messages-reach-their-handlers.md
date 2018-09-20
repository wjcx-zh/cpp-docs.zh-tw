---
title: 非命令訊息如何連接其處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b5c38a1d4294993170cfeff64be6a83700fa7497
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373434"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>非命令訊息如何連接其處理常式

與命令不同，標準 Windows 訊息不會透過鏈結的命令目標路由，但通常都由 Windows 會傳送訊息的視窗。 視窗可能是主框架視窗、 的 MDI 子視窗，為標準控制項、 對話方塊、 檢視或某種其他類型的子視窗。

在執行階段，每個 Windows 視窗附加至視窗物件 (直接或間接衍生自`CWnd`) 具有自己的相關聯的訊息對應和處理常式函式。 架構會使用訊息對應，與命令，將內送訊息對應至處理常式。

## <a name="see-also"></a>另請參閱

[架構如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)

