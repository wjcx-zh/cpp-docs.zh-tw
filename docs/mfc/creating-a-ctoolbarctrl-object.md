---
title: 建立 CToolBarCtrl 物件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CToolBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c98f99ef7ff26fed7d7df89881d2148af6bc993a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421644"
---
# <a name="creating-a-ctoolbarctrl-object"></a>建立 CToolBarCtrl 物件

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)物件包含數個內部資料結構，一份按鈕的影像點陣圖、 一份按鈕標籤字串，以及一份`TBBUTTON`結構 —，建立關聯的映像及/或字串的位置、 樣式、 狀態，並按鈕的命令識別碼。 每個這些資料結構的項目被指以零為起始的索引。 您可以使用之前`CToolBarCtrl`物件時，您必須設定這些資料結構。 如需資料結構的清單，請參閱 <<c0> [ 工具列上的控制項](controls-mfc.md)Windows SDK 中。 字串清單，僅適用於按鈕標籤;您無法從工具列，來擷取字串。

若要使用 `CToolBarCtrl` 物件，您通常會執行下列步驟：

### <a name="to-use-a-ctoolbarctrl-object"></a>使用 CToolBarCtrl 物件

1. 建構[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)物件。

1. 呼叫[Create](../mfc/reference/ctoolbarctrl-class.md#create)建立 Windows 工具列通用控制項，並將其附加至`CToolBarCtrl`物件。 如果您想點陣圖影像的按鈕時，將按鈕點陣圖加入工具列藉由呼叫[AddBitmap](../mfc/reference/ctoolbarctrl-class.md#addbitmap)。 如果您想字串標籤的按鈕時，將字串加入至工具列藉由呼叫[AddString](../mfc/reference/ctoolbarctrl-class.md#addstring)及/或[AddStrings](../mfc/reference/ctoolbarctrl-class.md#addstrings)。 之後呼叫`AddString`及/或`AddStrings`，您應該呼叫[AutoSize](../mfc/reference/ctoolbarctrl-class.md#autosize)若要取得的字串或字串才會出現。

1. 新增至工具列按鈕結構，藉由呼叫[AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)。

1. 如果您想要的工具提示，處理**TTN_NEEDTEXT**工具列的 [擁有者] 視窗中的訊息中所述[處理工具提示通知](../mfc/handling-tool-tip-notifications.md)。

1. 如果您想讓使用者能夠自訂工具列時，處理是主控視窗中的自訂通知訊息中所述[處理自訂告知](../mfc/handling-customization-notifications.md)。

## <a name="see-also"></a>另請參閱

[使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

