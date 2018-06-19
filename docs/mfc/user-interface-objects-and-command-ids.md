---
title: 使用者介面物件和命令 Id |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts, associating with IDs
- MFC, command routing
- toolbar controls [MFC], command ID
- menu items, associating with IDs
- user interface objects [MFC], associating with IDs
- command IDs, user interface objects
- command routing [MFC], MFC
- command handling [MFC], user-interface objects
ms.assetid: 4ea19e9b-ed1e-452e-bd33-7f509107a45b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b56babf0e42dde521a6bda3a7d9713db519182c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385595"
---
# <a name="user-interface-objects-and-command-ids"></a>使用者介面物件和命令 ID
功能表項目、工具列按鈕和快速鍵是能夠產生命令的「使用者介面物件」。 每一個這類使用者介面物件均具有 ID. 您可透過指派相同的 ID 給物件和命令，來建立使用者介面物件和命令的關聯。 中所述[訊息](../mfc/messages.md)，命令會實作為特殊訊息。 以下「架構中的命令」一圖中顯示架構如何管理命令。 當使用者介面物件產生命令時 (例如 `ID_EDIT_CLEAR_ALL`，應用程式中的其中一個物件會如下圖處理命令)，即透過文件的訊息對應呼叫文件物件的 `OnEditClearAll` 函式。  
  
 ![架構中的命令](../mfc/media/vc385p1.gif "vc385p1")  
Framework 中的命令  
  
 以下「架構中的命令更新」一圖中顯示 MFC 如何更新使用者介面物件 (例如，功能表項目和工具列按鈕)。 在功能表下拉之前，或者在工具列按鈕的閒置迴圈期間，MFC 會路由更新命令。 在下圖中，資料物件會呼叫其更新命令處理常式 `OnUpdateEditClearAll`，以啟用或停用使用者介面物件。  
  
 ![命令在架構中更新](../mfc/media/vc385p2.png "vc385p2")  
架構中的命令更新  
  
## <a name="see-also"></a>另請參閱  
 [架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)

