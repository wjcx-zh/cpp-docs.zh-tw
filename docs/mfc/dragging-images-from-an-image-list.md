---
title: 從影像清單拖曳影像
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], dragging images from
- dragging images from image lists [MFC]
- image lists [MFC], dragging images from
- images [MFC], dragging from image lists
ms.assetid: af691db8-e4f0-4046-b7b9-9acc68d3713d
ms.openlocfilehash: 9d42e9cdd8e2711fc6ed6aa0d08a19b8bc55d5f1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562197"
---
# <a name="dragging-images-from-an-image-list"></a>從影像清單拖曳影像

[CImageList](../mfc/reference/cimagelist-class.md)包含螢幕上拖曳影像的函式。 拖曳函式平滑且沒有游標閃爍地移動彩色影像。 遮罩影像和未遮罩影像都可以拖曳。

[BeginDrag](../mfc/reference/cimagelist-class.md#begindrag)成員函式開始拖曳作業。 參數包含要拖曳的影像的索引和在影像中作用點的位置。 作用點是拖曳函式辨認為影像的實際螢幕位置的單一像素。 一般而言，應用程式設定作用點，以便使其與滑鼠游標的作用點相符。 [DragMove](../mfc/reference/cimagelist-class.md#dragmove)成員函式會將影像移到新位置。

[DragEnter](../mfc/reference/cimagelist-class.md#dragenter)成員函式 視窗內設定拖曳影像的初始位置，並繪製影像的位置。 參數包含要在其中繪製影像的視窗的指標，以及指定視窗內的初始位置座標的點。 座標是相對於視窗左上角，而非工作區。 這也適用於接受座標做為參數的所有影像拖曳函式。 這表示指定座標時，您必須補償視窗項目的寬度，例如框線、標題列和功能表列。 如果您指定**NULL**呼叫時的視窗控制代碼`DragEnter`、 拖曳函式與桌面視窗中，相關聯的裝置內容中繪製影像，而且座標是相對於螢幕左上角。

`DragEnter` 在拖曳作業期間鎖定特定視窗的其他更新。 如果您要在拖曳作業，例如反白顯示拖放作業時，目標期間進行繪圖您可以使用暫時隱藏被拖曳的影像[DragLeave](../mfc/reference/cimagelist-class.md#dragleave)成員函式。 您也可以使用[DragShowNoLock](../mfc/reference/cimagelist-class.md#dragshownolock)成員函式。

呼叫[EndDrag](../mfc/reference/cimagelist-class.md#enddrag)當您完成拖曳影像。

[SetDragCursorImage](../mfc/reference/cimagelist-class.md#setdragcursorimage)成員函式會藉由結合特定的映像 （通常是滑鼠游標影像） 與目前拖曳影像來建立新的拖曳影像。 由於拖曳函式會使用新的映像，在拖曳作業期間，您應該使用 Windows [ShowCursor](/windows/desktop/api/winuser/nf-winuser-showcursor)函式來呼叫之後隱藏實際滑鼠游標`SetDragCursorImage`。 否則，系統可能會在拖曳作業期間出現兩個滑鼠游標。

當應用程式呼叫 `BeginDrag`時，系統會建立暫存、內部影像清單，並將指定的影像拖曳複製到內部清單。 您可以使用，以擷取暫存拖曳影像清單的指標[GetDragImage](../mfc/reference/cimagelist-class.md#getdragimage)成員函式。 函式也會擷取目前拖曳位置以及拖曳影像相對於拖曳位置的位移。

## <a name="see-also"></a>另請參閱

[使用 CImageList](../mfc/using-cimagelist.md)<br/>
[控制項](../mfc/controls-mfc.md)

