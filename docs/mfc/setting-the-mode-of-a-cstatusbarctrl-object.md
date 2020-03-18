---
title: 設定 CStatusBarCtrl 物件的模式
ms.date: 11/04/2016
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
ms.openlocfilehash: 79b499533196447898ce62ea9dc86c1674fc0302
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446414"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>設定 CStatusBarCtrl 物件的模式

`CStatusBarCtrl` 物件有兩種模式： simple 和簡單。 在大部分的情況下，您的狀態列控制項將會有一或多個元件，以及文字，可能是圖示或圖示。 這稱為簡單模式。 如需此模式的詳細資訊，請參閱[初始化 CStatusBarCtrl 物件的元件](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md)。

不過，在某些情況下，您只需要顯示一行文字。 在此情況下，簡單模式就足以滿足您的需求。 若要將 `CStatusBarCtrl` 物件的模式變更為 simple，請呼叫[SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple)成員函式。 當狀態列控制項處於簡單模式後，請呼叫 `SetText` 成員函式來設定文字，傳遞255做為*nPane*參數的值。

您可以使用[IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple)函數來判斷 `CStatusBarCtrl` 物件所在的模式。

> [!NOTE]
>  如果狀態列物件從簡單變更為 simple，或反之亦然，則會立即重新繪製視窗，如果適用的話，會自動還原任何已定義的元件。

## <a name="see-also"></a>另請參閱

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
