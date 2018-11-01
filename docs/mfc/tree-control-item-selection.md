---
title: 樹狀目錄控制項目選取
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
ms.openlocfilehash: bd3ade31ce1e41481943659ba9a8ef8dd77117fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592701"
---
# <a name="tree-control-item-selection"></a>樹狀目錄控制項目選取

當選取項目變更從一個項目到另一個，樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 會傳送[TVN_SELCHANGING](/windows/desktop/Controls/tvn-selchanging)並[TVN_SELCHANGED](/windows/desktop/Controls/tvn-selchanged)通知訊息。 兩個通知均包含一個值，該值指定變更為按一下滑鼠或是按下按鍵的結果。 通知還包含取得選取範圍的項目和遺失選取範圍的項目的相關資訊。 您可以使用這項資訊來設定項目屬性，而其屬性則視項目的選取狀態而定。 傳回 **，則為 TRUE**來回`TVN_SELCHANGING`防止選取範圍變更; 傳回**FALSE**允許變更。

應用程式可以變更選取項目，藉由呼叫[SelectItem](../mfc/reference/ctreectrl-class.md#selectitem)成員函式。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

