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
ms.openlocfilehash: 366f0e2953e5190f80a2877804bff2fc7dbbd520
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372781"
---
# <a name="scrolling-and-scaling-views"></a>捲動和縮放檢視

MFC 支援捲動的檢視和自動縮放到顯示這些檢視的幀視窗大小的檢視。 類`CScrollView`支援這兩種視圖。

有關滾動和縮放的詳細資訊,請參閱*MFC 參考*中的[CScrollView](../mfc/reference/cscrollview-class.md)類。 有關滾動示例,請參閱[塗鴉範例](../overview/visual-cpp-samples.md)。

## <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- 捲動檢視

- 縮放檢視

- [檢視座標](/windows/win32/gdi/window-coordinate-system)

## <a name="scrolling-a-view"></a><a name="_core_scrolling_a_view"></a>捲動檢視

通常,文檔的大小大於其檢視可以顯示的大小。 這可能是因為文件的數據增加或用戶收縮設置視圖的視窗。 在這種情況下,視圖必須支援滾動。

任何檢視都可以在其`OnHScroll`和`OnVScroll`成員函數中處理滾動條消息。 您可以在這些函數中實現滾動條消息處理,自己執行所有工作,也可以使用類`CScrollView`為您處理滾動。

`CScrollView` 會執行下列動作：

- 視窗管理視窗與視埠大小與映射模式

- 自動捲動以回應捲動條訊息

您可以指定「頁面」(當使用者在滾動條軸中按一下時)和「行」(當使用者在滾動箭頭中按一下時)的滾動量。 規劃這些值以適應視圖的性質。 例如,您可能希望以 1 圖元的增量滾動圖形檢視,但基於文本文檔中的行高度以增量滾動。

## <a name="scaling-a-view"></a><a name="_core_scaling_a_view"></a>縮放檢視

當希望檢視自動適合其框架視窗的大小時,可以使用`CScrollView`縮放而不是滾動。 邏輯視圖將拉伸或收縮,以完全適合視窗的工作區。 縮放視圖沒有滾動條。

## <a name="see-also"></a>另請參閱

[使用檢視](../mfc/using-views.md)
