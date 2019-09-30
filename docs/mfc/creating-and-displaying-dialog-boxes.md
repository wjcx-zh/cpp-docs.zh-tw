---
title: 建立和顯示對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
ms.openlocfilehash: 6d23e4d2c9249ce248eb8092963036f2ba5cacac
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685743"
---
# <a name="creating-and-displaying-dialog-boxes"></a>建立和顯示對話方塊

建立對話方塊物件作業分成兩個階段。 首先，建構對話方塊物件，然後建立對話方塊視窗。 強制回應和非強制回應對話方塊各用於建立並顯示對話方塊視窗的處理序不盡相同。 下表列出強制回應和非強制回應對話方塊通常建構及顯示的方式。

### <a name="dialog-creation"></a>建立對話方塊

|對話方塊類型|建立方式|
|-----------------|----------------------|
|[獨佔](../mfc/creating-modeless-dialog-boxes.md)|建構 `CDialog`，然後呼叫 `Create` 成員函式。|
|[強制回應](../mfc/creating-modal-dialog-boxes.md)|建構 `CDialog`，然後呼叫 `DoModal` 成員函式。|

如有需要，您可以從已建立的[記憶體中對話方塊範本](../mfc/using-a-dialog-template-in-memory.md)，而不是從對話方塊範本資源建立對話方塊。 這是進階主題。

## <a name="see-also"></a>另請參閱

[在 MFC 中使用對話方塊](../mfc/life-cycle-of-a-dialog-box.md)
