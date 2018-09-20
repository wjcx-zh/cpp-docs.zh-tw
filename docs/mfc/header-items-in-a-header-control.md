---
title: 標題控制項中的標頭項目 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- header controls [MFC], header items in
- header items in header controls [MFC]
- CHeaderCtrl class [MFC], header items in
- controls [MFC], header
ms.assetid: ac79ef1f-a671-4ab2-93e9-b1aa016a48bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 21f1893861c5cb6a134cffa75806cc53eadaf059
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442366"
---
# <a name="header-items-in-a-header-control"></a>標題控制項中的標題項目

您有相當大的控制權的外觀和行為的標頭項目組成標題控制項 ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md))。 每個標題項目可以有字串、點陣圖影像、來自相關聯影像清單的影像，或與其關聯之應用程式所定義的 32 位元值。 字串、點陣圖或影像會在標題項目中顯示。

您藉由呼叫建立時可以自訂外觀和內容的新項目[cheaderctrl:: Insertitem](../mfc/reference/cheaderctrl-class.md#insertitem) ，或修改現有的項目，藉由呼叫[cheaderctrl:: Getitem](../mfc/reference/cheaderctrl-class.md#getitem)並[Cheaderctrl:: Setitem](../mfc/reference/cheaderctrl-class.md#setitem)。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [自訂標頭項目的外觀](../mfc/customizing-the-header-item-s-appearance.md)

- [排序標題控制項中的項目](../mfc/ordering-items-in-the-header-control.md)

- [為標題項目提供拖放支援](../mfc/providing-drag-and-drop-support-for-header-items.md)

- [使用影像清單與標題控制項](../mfc/using-image-lists-with-header-controls.md)

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)

