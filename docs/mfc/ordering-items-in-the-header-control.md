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
ms.openlocfilehash: bae351d921c25993d6b7029f9052e1938179673b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392646"
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
