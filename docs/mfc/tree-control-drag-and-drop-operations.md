---
title: 樹狀目錄控制項拖放作業 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a620c2481b29b80f6d30dd6457716a652f51fd85
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="tree-control-drag-and-drop-operations"></a>樹狀目錄控制項拖放作業
樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 會傳送通知，當使用者開始拖曳項目。 控制項傳送[TVN_BEGINDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773504)通知訊息，當使用者開始拖曳項目具有滑鼠左鍵和[TVN_BEGINRDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773509)通知訊息，當使用者開始拖曳[右] 按鈕。 您可以防止樹狀控制項傳送這些通知樹狀目錄控制項**TVS_DISABLEDRAGDROP**樣式。  
  
 取得要顯示在拖曳作業期間藉由呼叫影像[CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage)成員函式。 樹狀控制項會根據被拖曳的項目之標籤產生拖曳點陣圖。 接著樹狀目錄控制項建立影像清單、 加入點陣圖至其中，然後將指標傳回至[CImageList](../mfc/reference/cimagelist-class.md)物件。  
  
 您必須提供實際拖曳項目的程式碼。 這通常牽涉到使用影像清單函式的拖曳功能和處理[WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616)和[WM_LBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms645608) (或[WM_RBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms646243))在拖曳作業開始之後所傳送的訊息。 如需映像清單函式的詳細資訊，請參閱[CImageList](../mfc/reference/cimagelist-class.md)中*MFC 參考*和[影像清單](http://msdn.microsoft.com/library/windows/desktop/bb761389)Windows SDK 中。 如需拖曳樹狀目錄控制項目的詳細資訊，請參閱[拖曳樹狀檢視項目](http://msdn.microsoft.com/library/windows/desktop/bb760017)，此外，在[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
 如果在樹狀控制項中的項目是拖放作業的目標，您需要知道滑鼠游標何時位於目標項目上。 您可以藉由呼叫找出[HitTest](../mfc/reference/ctreectrl-class.md#hittest)成員函式。 您指定的點和整數或位址[TVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb773448)結構，其中包含滑鼠游標目前座標。 當函式傳回時，整數或結構會包含一個旗標，表示相對於樹狀控制項的滑鼠游標位置。 如果游標位於樹狀控制項中的項目上，結構也會包含該項目的控制代碼。  
  
 您可以指定項目是拖放作業的目標，藉由呼叫[SetItem](../mfc/reference/ctreectrl-class.md#setitem)成員函式來將狀態設定為`TVIS_DROPHILITED`值。 具有這個狀態的項目會繪製為用來表示拖放目標的樣式。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)

