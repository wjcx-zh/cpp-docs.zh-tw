---
title: 標題控制項中的標題項目
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], header items in
- header items in header controls [MFC]
- CHeaderCtrl class [MFC], header items in
- controls [MFC], header
ms.assetid: ac79ef1f-a671-4ab2-93e9-b1aa016a48bf
ms.openlocfilehash: a70d1d9225d2ac8ef2f7ed3ad9f603a64a937bc7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620095"
---
# <a name="header-items-in-a-header-control"></a>標題控制項中的標題項目

您對組成標題控制項之標頭專案的外觀和行為有相當大的控制（[CHeaderCtrl](reference/cheaderctrl-class.md)）。 每個標題項目可以有字串、點陣圖影像、來自相關聯影像清單的影像，或與其關聯之應用程式所定義的 32 位元值。 字串、點陣圖或影像會在標題項目中顯示。

您可以藉由呼叫[CHeaderCtrl：： InsertItem](reference/cheaderctrl-class.md#insertitem)或修改現有的專案來自訂新專案的外觀和內容，方法是對[CHeaderCtrl：： GetItem](reference/cheaderctrl-class.md#getitem)和[CHeaderCtrl：： SetItem](reference/cheaderctrl-class.md#setitem)進行呼叫。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [自訂標題專案的外觀](customizing-the-header-item-s-appearance.md)

- [排序標題控制項中的專案](ordering-items-in-the-header-control.md)

- [為標題項目提供拖放支援](providing-drag-and-drop-support-for-header-items.md)

- [搭配使用影像清單與標題控制項](using-image-lists-with-header-controls.md)

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](using-cheaderctrl.md)
