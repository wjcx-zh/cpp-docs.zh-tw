---
title: "從影像清單拖曳影像 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], dragging images from
- dragging images from image lists [MFC]
- image lists [MFC], dragging images from
- images [MFC], dragging from image lists
ms.assetid: af691db8-e4f0-4046-b7b9-9acc68d3713d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 792f112952493fe1ee86d52a6a235604ebee9db5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="dragging-images-from-an-image-list"></a>從影像清單拖曳影像
[CImageList](../mfc/reference/cimagelist-class.md)包含在螢幕上拖曳影像的函式。 拖曳函式平滑且沒有游標閃爍地移動彩色影像。 遮罩影像和未遮罩影像都可以拖曳。  
  
 [BeginDrag](../mfc/reference/cimagelist-class.md#begindrag)成員函式開始拖曳作業。 參數包含要拖曳的影像的索引和在影像中作用點的位置。 作用點是拖曳函式辨認為影像的實際螢幕位置的單一像素。 一般而言，應用程式設定作用點，以便使其與滑鼠游標的作用點相符。 [DragMove](../mfc/reference/cimagelist-class.md#dragmove)成員函式將影像移到新位置。  
  
 [DragEnter](../mfc/reference/cimagelist-class.md#dragenter)成員函式在視窗內設定拖曳影像的初始位置，並繪製影像的位置。 參數包含要在其中繪製影像的視窗的指標，以及指定視窗內的初始位置座標的點。 座標是相對於視窗左上角，而非工作區。 這也適用於接受座標做為參數的所有影像拖曳函式。 這表示指定座標時，您必須補償視窗項目的寬度，例如框線、標題列和功能表列。 如果您指定**NULL**呼叫時的視窗控制代碼`DragEnter`、 拖曳函式桌面視窗中，與相關聯的裝置內容中繪製影像，而且座標是相對於螢幕左上角。  
  
 `DragEnter` 在拖曳作業期間鎖定特定視窗的其他更新。 如果您需要在拖曳作業，例如反白顯示拖放作業的目標期間進行繪圖可以暫時隱藏被拖曳的影像使用[DragLeave](../mfc/reference/cimagelist-class.md#dragleave)成員函式。 您也可以使用[DragShowNoLock](../mfc/reference/cimagelist-class.md#dragshownolock)成員函式。  
  
 呼叫[EndDrag](../mfc/reference/cimagelist-class.md#enddrag)完成拖曳影像。  
  
 [SetDragCursorImage](../mfc/reference/cimagelist-class.md#setdragcursorimage)成員函式會建立新的拖曳影像，藉由結合特定的映像 （通常是滑鼠游標影像） 與目前拖曳影像。 由於拖曳函式在拖曳作業期間使用新的映像，您應該使用 Windows [ShowCursor](http://msdn.microsoft.com/library/windows/desktop/ms648396)函式呼叫之後隱藏實際滑鼠游標`SetDragCursorImage`。 否則，系統可能會在拖曳作業期間出現兩個滑鼠游標。  
  
 當應用程式呼叫 `BeginDrag`時，系統會建立暫存、內部影像清單，並將指定的影像拖曳複製到內部清單。 您可以使用，以擷取暫存拖曳影像清單的指標[GetDragImage](../mfc/reference/cimagelist-class.md#getdragimage)成員函式。 函式也會擷取目前拖曳位置以及拖曳影像相對於拖曳位置的位移。  
  
## <a name="see-also"></a>請參閱  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控制項](../mfc/controls-mfc.md)

