---
title: 從影像清單拖曳影像
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], dragging images from
- dragging images from image lists [MFC]
- image lists [MFC], dragging images from
- images [MFC], dragging from image lists
ms.assetid: af691db8-e4f0-4046-b7b9-9acc68d3713d
ms.openlocfilehash: 5d15b0b66d2270174dbfbcfd21bb77f5f41558c7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626477"
---
# <a name="dragging-images-from-an-image-list"></a>從影像清單拖曳影像

[CImageList](reference/cimagelist-class.md)包含在螢幕上拖曳影像的函式。 拖曳函式平滑且沒有游標閃爍地移動彩色影像。 遮罩影像和未遮罩影像都可以拖曳。

[BeginDrag](reference/cimagelist-class.md#begindrag)成員函式會開始拖曳作業。 參數包含要拖曳的影像的索引和在影像中作用點的位置。 作用點是拖曳函式辨認為影像的實際螢幕位置的單一像素。 一般而言，應用程式設定作用點，以便使其與滑鼠游標的作用點相符。 [DragMove](reference/cimagelist-class.md#dragmove)成員函式會將影像移至新的位置。

[System.windows.dragdrop.dragenter>](reference/cimagelist-class.md#dragenter)成員函式會設定拖曳影像在視窗中的初始位置，並在該位置繪製影像。 參數包含要在其中繪製影像的視窗的指標，以及指定視窗內的初始位置座標的點。 座標是相對於視窗左上角，而非工作區。 這也適用於接受座標做為參數的所有影像拖曳函式。 這表示指定座標時，您必須補償視窗項目的寬度，例如框線、標題列和功能表列。 如果您在呼叫時指定**Null**視窗控制碼 `DragEnter` ，拖曳函式會在與桌面視窗相關聯的裝置內容中繪製影像，而座標則是相對於螢幕的左上角。

`DragEnter` 在拖曳作業期間鎖定特定視窗的其他更新。 如果您需要在拖曳作業期間執行任何繪圖，例如反白顯示拖放作業的目標，您可以使用[DragLeave](reference/cimagelist-class.md#dragleave)成員函式，暫時隱藏拖曳的影像。 您也可以使用[DragShowNoLock](reference/cimagelist-class.md#dragshownolock)成員函式。

當您完成拖曳影像時，請呼叫[EndDrag](reference/cimagelist-class.md#enddrag) 。

[SetDragCursorImage](reference/cimagelist-class.md#setdragcursorimage)成員函式會將指定的影像（通常是滑鼠游標影像）與目前的拖曳影像結合，以建立新的拖曳影像。 因為拖曳函式會在拖曳作業期間使用新的影像，所以您應該在呼叫之後，使用 Windows [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor)函式來隱藏實際的滑鼠游標 `SetDragCursorImage` 。 否則，系統可能會在拖曳作業期間出現兩個滑鼠游標。

當應用程式呼叫 `BeginDrag`時，系統會建立暫存、內部影像清單，並將指定的影像拖曳複製到內部清單。 您可以使用[GetDragImage](reference/cimagelist-class.md#getdragimage)成員函式，抓取暫存拖曳影像清單的指標。 函式也會擷取目前拖曳位置以及拖曳影像相對於拖曳位置的位移。

## <a name="see-also"></a>另請參閱

[使用 CImageList](using-cimagelist.md)<br/>
[控制項](controls-mfc.md)
