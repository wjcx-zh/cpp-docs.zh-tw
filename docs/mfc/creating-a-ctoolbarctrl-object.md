---
title: "建立 CToolBarCtrl 物件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CToolBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e86fad8191c4dea2eed3ae34ec96ed853ac1deae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-ctoolbarctrl-object"></a>建立 CToolBarCtrl 物件
[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)物件包含數個內部資料結構 — 一份按鈕影像點陣圖、 的按鈕標籤字串清單，以及一份`TBBUTTON`結構 — 的關聯一個影像和/或字串的位置、 樣式、 狀態和按鈕的命令識別碼。 每個這些資料結構的項目都有以零為起始的索引。 您可以使用之前`CToolBarCtrl`物件，您必須設定這些資料結構。 如需資料結構的清單，請參閱[工具列控制項](controls-mfc.md)Windows SDK 中。 字串清單，只可以用於按鈕標籤。您無法從工具列擷取字串。  
  
 若要使用 `CToolBarCtrl` 物件，您通常會執行下列步驟：  
  
### <a name="to-use-a-ctoolbarctrl-object"></a>若要使用 CToolBarCtrl 物件  
  
1.  建構[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)物件。  
  
2.  呼叫[建立](../mfc/reference/ctoolbarctrl-class.md#create)建立 Windows 工具列通用控制項並將其附加至`CToolBarCtrl`物件。 如果您想點陣圖影像的按鈕，將按鈕點陣圖加入工具列藉由呼叫[AddBitmap](../mfc/reference/ctoolbarctrl-class.md#addbitmap)。 如果您想字串標籤按鈕，將字串加入至工具列藉由呼叫[AddString](../mfc/reference/ctoolbarctrl-class.md#addstring)及/或[AddStrings](../mfc/reference/ctoolbarctrl-class.md#addstrings)。 在呼叫`AddString`及/或`AddStrings`，您應該呼叫[AutoSize](../mfc/reference/ctoolbarctrl-class.md#autosize)以取得字串或字串出現。  
  
3.  藉由呼叫在工具列上加入按鈕結構[AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)。  
  
4.  如果您想要的工具提示，處理**TTN_NEEDTEXT**工具列的主控視窗中的訊息中所述[處理工具提示通知](../mfc/handling-tool-tip-notifications.md)。  
  
5.  如果您想讓使用者能夠自訂工具列時，處理是主控視窗中的自訂通知訊息中所述[處理自訂告知](../mfc/handling-customization-notifications.md)。  
  
## <a name="see-also"></a>請參閱  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

