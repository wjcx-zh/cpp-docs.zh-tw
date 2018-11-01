---
title: 排序標題控制項中的項目
ms.date: 11/04/2016
f1_keywords:
- DS_DRAGDROP
helpviewer_keywords:
- sequence [MFC]
- sequence [MFC], header control items
- OrderToIndex method [MFC]
- DS_DRAGDROP notification [MFC]
- GetOrderArray method [MFC]
- SetOrderArray method [MFC]
- header controls [MFC], ordering items
ms.assetid: 5aaef872-75b5-49c5-8fed-6f9a81fca812
ms.openlocfilehash: 5c4fef821efa697d41bf02ef1891efcf0fa21d4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583504"
---
# <a name="ordering-items-in-the-header-control"></a>排序標題控制項中的項目

之後，您就[項目新增至標題控制項](../mfc/adding-items-to-the-header-control.md)，您可以操作或取得它們的順序，使用下列函式的相關資訊：

- [Cheaderctrl:: Getorderarray](../mfc/reference/cheaderctrl-class.md#getorderarray)和[cheaderctrl:: Setorderarray](../mfc/reference/cheaderctrl-class.md#setorderarray)

   以由左至右的順序擷取和設定標題項目。

- [CHeaderCtrl::OrderToIndex](../mfc/reference/cheaderctrl-class.md#ordertoindex)。

   擷取特定標頭項目的索引值。

除了先前的成員函式，HDS_DRAGDROP 樣式可讓使用者拖放標題控制項內的標頭項目。 如需詳細資訊，請參閱 <<c0> [ 提供的標頭項目拖放支援](../mfc/providing-drag-and-drop-support-for-header-items.md)。

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)

