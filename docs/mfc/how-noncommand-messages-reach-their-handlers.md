---
title: "非命令訊息如何連接其處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0e6a6f30597ddb5ea68b3a5a00c35e27024fb9b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>非命令訊息如何連接其處理常式
與命令不同，標準 Windows 訊息不會透過鏈結的命令目標路由，但通常會由 Windows 會傳送訊息的視窗。 視窗可能是主框架視窗、 MDI 子視窗、 標準控制項、 對話方塊、 檢視或其他種類之子視窗。  
  
 在執行階段，每個 Windows 視窗連接至視窗物件 (直接或間接衍生自`CWnd`) 具有自己的相關聯的訊息對應和處理常式函式。 架構會使用訊息對應 — 命令，將內送訊息對應至處理常式。  
  
## <a name="see-also"></a>另請參閱  
 [架構如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)

