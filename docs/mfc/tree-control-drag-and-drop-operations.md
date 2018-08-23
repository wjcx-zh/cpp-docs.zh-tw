---
title: 樹狀目錄控制項拖放作業 |Microsoft Docs
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
ms.openlocfilehash: 9e1c642642f94c021001ae67d2dcc3fd87f4f287
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589081"
---
# <a name="tree-control-drag-and-drop-operations"></a>樹狀目錄控制項拖放作業
樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 會傳送通知，當使用者開始拖曳項目。 控制項會傳送[TVN_BEGINDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773504)當使用者開始拖曳滑鼠左鍵的項目時，會產生通知訊息。 並[TVN_BEGINRDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773509)使用者開始拖曳時，會產生通知訊息。右邊的按鈕。 您可以防止樹狀目錄控制項提供 TVS_DISABLEDRAGDROP 樣式的樹狀控制項傳送這些通知。  
  
 取得要顯示在拖曳作業期間，藉由呼叫影像[CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage)成員函式。 樹狀控制項會根據被拖曳的項目之標籤產生拖曳點陣圖。 然後樹狀結構控制項中建立影像清單、 加入點陣圖至它，並將指標傳回至[CImageList](../mfc/reference/cimagelist-class.md)物件。  
  
 您必須提供實際拖曳項目的程式碼。 這通常牽涉到使用影像清單函式的拖曳功能和處理[WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616)並[WM_LBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms645608) (或[WM_RBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms646243))在拖曳作業開始後所傳送的訊息。 如需有關影像清單函式的詳細資訊，請參閱[CImageList](../mfc/reference/cimagelist-class.md)中*MFC 參考 》* 並[影像清單](http://msdn.microsoft.com/library/windows/desktop/bb761389)Windows SDK 中。 如需拖曳樹狀目錄控制項目的詳細資訊，請參閱 <<c0> [ 拖曳樹狀檢視項目](http://msdn.microsoft.com/library/windows/desktop/bb760017)，也在 Windows SDK 中。  
  
 如果在樹狀控制項中的項目是拖放作業的目標，您需要知道滑鼠游標何時位於目標項目上。 您可以藉由呼叫了[HitTest](../mfc/reference/ctreectrl-class.md#hittest)成員函式。 您指定的點和整數或位址[TVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb773448)結構，其中包含滑鼠游標目前座標。 當函式傳回時，整數或結構會包含一個旗標，表示相對於樹狀控制項的滑鼠游標位置。 如果游標位於樹狀控制項中的項目上，結構也會包含該項目的控制代碼。  
  
 您可以指定項目是拖放作業的目標，藉由呼叫[SetItem](../mfc/reference/ctreectrl-class.md#setitem)成員函式來將狀態設定為`TVIS_DROPHILITED`值。 具有這個狀態的項目會繪製為用來表示拖放目標的樣式。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)

