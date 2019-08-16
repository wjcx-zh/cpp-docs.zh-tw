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
ms.openlocfilehash: 7064880c5ceef8e7dc3e35bb7ef5bc700b0842d2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511225"
---
# <a name="scrolling-and-scaling-views"></a>捲動和縮放檢視

MFC 支援的視圖會自動調整為顯示它們的框架視窗大小的捲軸和視圖。 類別`CScrollView`支援這兩種類型的視圖。

如需有關滾動和縮放的詳細資訊, 請參閱*MFC 參考*中的類別[CScrollView](../mfc/reference/cscrollview-class.md) 。 如需滾動範例, 請參閱「[塗抹」範例](../overview/visual-cpp-samples.md)。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- 滾動視圖

- 縮放視圖

- [視圖座標](/windows/win32/gdi/window-coordinate-system)

##  <a name="_core_scrolling_a_view"></a>滾動視圖

檔的大小經常大於其 view 可以顯示的大小。 發生這種情況的原因可能是檔的資料增加, 或是使用者縮小了框架的視窗。 在這種情況下, 此視圖必須支援滾動。

任何視圖都可以處理其`OnHScroll`和`OnVScroll`成員函式中的捲軸訊息。 您可以在這些函式中執行捲軸訊息處理、自行執行所有工作, 或者您可以使用`CScrollView`類別來處理您的滾動。

`CScrollView` 會執行下列動作：

- 管理視窗和視口大小和對應模式

- 自動滾動以回應捲軸訊息

您可以指定要對「頁面」 (當使用者按一下捲軸軸時) 和「行」 (當使用者按一下滾動箭號時) 滾動的程度。 請規劃這些值, 以符合您的視圖本質。 例如, 您可能想要針對圖形視圖以1個圖元的增量滾動, 但根據文字檔中的行高, 以遞增。

##  <a name="_core_scaling_a_view"></a>縮放視圖

當您想要讓視圖自動調整其框架視窗的大小時, 您可以使用`CScrollView`進行縮放, 而不是捲軸。 邏輯視圖會伸展或縮小, 以完全符合視窗的工作區。 縮放的視圖沒有捲軸。

## <a name="see-also"></a>另請參閱

[使用檢視](../mfc/using-views.md)
