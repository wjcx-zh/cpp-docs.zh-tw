---
title: 初始化 CStatusBarCtrl 物件的組件
ms.date: 11/04/2016
helpviewer_keywords:
- CStatusBarCtrl class [MFC], simple mode
- status bars [MFC], declaring parts of
- simple status bars [MFC]
- status bars [MFC], icons
- status bars [MFC], simple mode
- icons, using in status bars
- CStatusBarCtrl class [MFC], declaring parts of
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
ms.openlocfilehash: a5b65a2bbb68eaa7058f3514bb95a5209a0e5e71
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444459"
---
# <a name="initializing-the-parts-of-a-cstatusbarctrl-object"></a>初始化 CStatusBarCtrl 物件的組件

根據預設，狀態列會使用不同的窗格顯示狀態資訊。 這些窗格 (也稱為組件) 可以包含文字字串、圖示或兩者。

使用[SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts)來定義狀態列會有多少部分和長度。 建立狀態列的元件之後，請呼叫[SetText](../mfc/reference/cstatusbarctrl-class.md#settext)和[SetIcon](../mfc/reference/cstatusbarctrl-class.md#seticon) ，以設定狀態列特定部分的文字或圖示。 成功設定組件後，會自動重新繪製控制項。

下列範例會初始化具有四個窗格的現有 `CStatusBarCtrl` 物件 (`m_StatusBarCtrl`)，然後在第二個組件中設定圖示 (IDI_ICON1) 和一些文字。

[!code-cpp[NVC_MFCControlLadenDialog#31](../mfc/codesnippet/cpp/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]

如需將 `CStatusBarCtrl` 物件的模式設定為 simple 的詳細資訊，請參閱[設定 CStatusBarCtrl 物件的模式](../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md)。

## <a name="see-also"></a>另請參閱

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
