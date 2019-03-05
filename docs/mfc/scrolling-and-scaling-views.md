---
title: 捲動和縮放檢視
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- scaling views [MFC]
- message handling [MFC], scroll bars in view class [MFC]
- scroll bars [MFC], messages
- scrolling views [MFC]
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
ms.openlocfilehash: 2baa89f233eb6df93cde3adbde35ba1e6d35c093
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283705"
---
# <a name="scrolling-and-scaling-views"></a>捲動和縮放檢視

MFC 支援檢視捲動和檢視表的自動調整，以顯示它們的框架視窗的大小。 類別`CScrollView`支援這兩種檢視。

如需有關捲動和縮放的詳細資訊，請參閱類別[CScrollView](../mfc/reference/cscrollview-class.md)中*MFC 參考 》*。 如需捲動的範例，請參閱 < [Scribble 範例](../visual-cpp-samples.md)。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- 捲動檢視

- 縮放檢視

- [檢視座標](/windows/desktop/gdi/window-coordinate-system)

##  <a name="_core_scrolling_a_view"></a> 捲動檢視

經常在文件的大小大於其檢視可以顯示的大小。 這可能是因為文件的資料會增加，或者使用者會縮小檢視的框架視窗。 在此情況下，檢視必須支援捲動。

任何檢視中可處理中的捲軸訊息及其`OnHScroll`和`OnVScroll`成員函式。 您可以在這些函式，其中一個實作捲軸訊息處理，自行執行所有的工作，或者您可以使用`CScrollView`類別來處理您捲動功能。

`CScrollView` 會執行下列動作：

- 管理視窗和檢視區大小和對應模式

- 自動捲動以因應捲軸的訊息

您可以指定多少捲動以檢視 「 頁面 」 （當使用者按一下捲軸中） 和"line"（當使用者按一下中的捲動箭號）。 規劃這些值以符合檢視的本質。 例如，您可能要捲動中 1 像素的增量，以圖形檢視，但根據文字文件中的列高度的增加。

##  <a name="_core_scaling_a_view"></a> 縮放檢視

當您想要自動配合其框架視窗的大小的檢視時，您可以使用`CScrollView`的調整，而非捲動。 邏輯檢視會延伸或縮小以完全配合視窗的工作區。 刻度的檢視有沒有捲軸。

## <a name="see-also"></a>另請參閱

[使用檢視](../mfc/using-views.md)
