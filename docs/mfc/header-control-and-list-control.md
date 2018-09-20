---
title: 標題控制項和清單控制項 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], with CHeaderCtrl
- CListCtrl class [MFC], header controls
- CHeaderCtrl class [MFC], with CListCtrl
- controls [MFC], header
- header controls [MFC]
- header controls [MFC], list controls used with
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 24d40ea26a6ff52490b4a501a8b62c0aace660b1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407630"
---
# <a name="header-control-and-list-control"></a>標題控制項和清單控制項

在大部分情況下，您將使用標題控制項中內嵌[CListCtrl](../mfc/reference/clistctrl-class.md)或是[CListView](../mfc/reference/clistview-class.md)物件。 不過，有不同的標頭控制項物件需要的例如操作排列在資料行或資料列中的資料的情況[CView](../mfc/reference/cview-class.md)-衍生物件。 在這些情況下，您需要更有效控制的外觀和內嵌的標題控制項的預設行為。

常見的情況下您想要提供標準標頭控制項時，預設行為，您可能想要使用[CListCtrl](../mfc/reference/clistctrl-class.md)或是[CListView](../mfc/reference/clistview-class.md)改。 使用`CListCtrl`要內嵌在清單檢視通用控制項的預設標題控制項的功能。 使用[CListView](../mfc/reference/clistview-class.md)當您想檢視物件中內嵌的預設標題控制項的功能。

> [!NOTE]
>  這些控制項只包含內建的標題控制項，如果在清單檢視控制項使用建立**LVS_REPORT**樣式。

在大部分情況下，變更內含的清單檢視控制項的樣式可以修改內嵌的標題控制項的外觀。 此外，可以透過父清單檢視控制項的成員函式取得標頭控制項的相關資訊。 不過，完整的控制權，並存取的屬性和樣式的內嵌的標題控制項中，建議取得標頭控制物件的指標。

內嵌的標題控制項物件可從其中`CListCtrl`或是`CListView`個別的類別呼叫`GetHeaderCtrl`成員函式。 下列程式碼示範：

[!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [使用影像清單與標題控制項](../mfc/using-image-lists-with-header-controls.md)

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

