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
ms.openlocfilehash: c4b4711729c6c3a4b63d4ad05252a5c49df98a0c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622127"
---
# <a name="ordering-items-in-the-header-control"></a>排序標題控制項中的項目

將[專案加入至標題控制項](adding-items-to-the-header-control.md)之後，您可以使用下列函數操作或取得其訂單的相關資訊：

- [CHeaderCtrl：： GetOrderArray](reference/cheaderctrl-class.md#getorderarray)和[CHeaderCtrl：： SetOrderArray](reference/cheaderctrl-class.md#setorderarray)

   以由左至右的順序擷取和設定標題項目。

- [CHeaderCtrl：： OrderToIndex](reference/cheaderctrl-class.md#ordertoindex)。

   擷取特定標頭項目的索引值。

除了先前的成員函式之外，HDS_DRAGDROP 樣式允許使用者拖放標題控制項內的標題專案。 如需詳細資訊，請參閱[針對標題專案提供拖放支援](providing-drag-and-drop-support-for-header-items.md)。

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](using-cheaderctrl.md)
