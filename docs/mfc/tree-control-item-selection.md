---
title: 樹狀目錄控制項目選取
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
ms.openlocfilehash: 07c7b673e0f9029f8ece928b0ab17760b3863cc7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513335"
---
# <a name="tree-control-item-selection"></a>樹狀目錄控制項目選取

當選取範圍從某個專案變更為另一個時, 樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 會傳送[TVN_SELCHANGING](/windows/win32/Controls/tvn-selchanging)和[TVN_SELCHANGED](/windows/win32/Controls/tvn-selchanged)通知訊息。 兩個通知均包含一個值，該值指定變更為按一下滑鼠或是按下按鍵的結果。 通知還包含取得選取範圍的項目和遺失選取範圍的項目的相關資訊。 您可以使用這項資訊來設定項目屬性，而其屬性則視項目的選取狀態而定。 傳回**TRUE**表示回應, `TVN_SELCHANGING`以防止選取範圍變更; 傳回**FALSE**則允許變更。

應用程式可以藉由呼叫[SelectItem](../mfc/reference/ctreectrl-class.md#selectitem)成員函式來變更選取範圍。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
