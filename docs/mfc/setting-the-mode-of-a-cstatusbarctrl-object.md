---
title: 設定 CStatusBarCtrl 物件的模式
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
ms.openlocfilehash: a6d1a0edb356f9737aa287809dd8bca4146c1854
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287930"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>設定 CStatusBarCtrl 物件的模式

有兩種模式`CStatusBarCtrl`物件： 簡單和非簡單。 在大部分的情況下，您的狀態列會有一或多個組件，以及文字和可能的圖示或圖示。 這稱為非簡單模式。 如需有關此模式的詳細資訊，請參閱[初始化 CStatusBarCtrl 物件的組件](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md)。

不過，有情況下，您只需要顯示單行文字。 在此情況下，簡單的模式是滿足您的需求。 若要變更的模式`CStatusBarCtrl`物件為 simple 時，呼叫[SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple)成員函式。 狀態列控制項是在簡單模式下，一旦設定文字，藉由呼叫`SetText`成員函式，傳遞做為值的 255 *nPane*參數。

您可以使用[IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple)函式來判斷哪一種模式`CStatusBarCtrl`物件。

> [!NOTE]
>  如果狀態列物件正在從簡單變更為 simple 時，或反之亦然，視窗立即重繪，且如果適用的話，請自動還原任何已定義的組件。

## <a name="see-also"></a>另請參閱

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
