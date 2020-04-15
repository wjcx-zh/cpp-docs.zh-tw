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
ms.openlocfilehash: e09a7bd274c44df2da48bbc007a95802fadd8cf0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365409"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>設定 CStatusBarCtrl 物件的模式

對象有兩`CStatusBarCtrl`種 模式:簡單和非簡單。 在大多數情況下,您的狀態列控制項將包含一個或多個部分,以及文本,以及圖示或圖示。 這稱為非簡單模式。 關於此模式的詳細資訊,請參閱[初始化 CStatusBarCtrl 物件的部分](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md)。

但是,在某些情況下,您只需要顯示一行文本。 在這種情況下,簡單模式足以滿足您的需要。 要將`CStatusBarCtrl`物件模式更改為簡單,請調用[SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple)成員函數。 狀態欄控件處於簡單模式后,通過調用`SetText`成員函數設置文本,傳遞 255 作為*nPane*參數的值。

可以使用[IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple)函數`CStatusBarCtrl`來確定 物件處於何種模式。

> [!NOTE]
> 如果狀態列物件從非簡單更改為簡單,反之亦然,則立即重新繪製視窗,如果適用,將自動還原任何定義的部件。

## <a name="see-also"></a>另請參閱

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
