---
title: 非命令訊息如何連接其處理常式 |Microsoft 文件
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
ms.openlocfilehash: 3999c74bf7a612acb998e7a044c12948d7679d9b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>非命令訊息如何連接其處理常式
與命令不同，標準 Windows 訊息不會透過鏈結的命令目標路由，但通常會由 Windows 會傳送訊息的視窗。 視窗可能是主框架視窗、 MDI 子視窗、 標準控制項、 對話方塊、 檢視或其他種類之子視窗。  
  
 在執行階段，每個 Windows 視窗連接至視窗物件 (直接或間接衍生自`CWnd`) 具有自己的相關聯的訊息對應和處理常式函式。 架構會使用訊息對應 — 命令，將內送訊息對應至處理常式。  
  
## <a name="see-also"></a>另請參閱  
 [架構如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)

