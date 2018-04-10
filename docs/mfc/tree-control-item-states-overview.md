---
title: 樹狀目錄控制項目狀態概觀 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- states, CTreeCtrl items
- tree controls [MFC], item states overview
- CTreeCtrl class [MFC], item states
ms.assetid: 2db11ae0-0d87-499d-8c1f-5e0dbe9e94c8
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6311169c0c8f9ee59f3582559f07ba85f997beff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-item-states-overview"></a>樹狀目錄控制項目狀態概觀
樹狀結構控制項中的每個項目 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 具有目前狀態。 例如，項目可選取、停用、展開等等。 在大部分的情況下，樹狀目錄控制項會自動設定項目的狀態以反映使用者動作，例如選擇項目。 不過，您也可以設定項目的狀態使用[SetItemState](../mfc/reference/ctreectrl-class.md#setitemstate)成員函式並擷取項目所使用的目前狀態[GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate)成員函式。 如需項目狀態的完整清單，請參閱[樹狀檢視控制項常數](http://msdn.microsoft.com/library/windows/desktop/bb759985)Windows SDK 中。  
  
 此項目的目前狀態是由 `nState` 參數指定。 樹狀目錄控制項可能會變更項目的狀態來反映自訂動作，例如選取項目或為項目設定焦點。 此外，應用程式可變更項目的狀態以停用或隱藏項目，或指定重疊影像或狀態影像。  
  
 當指定或變更項目的狀態時，`nStateMask` 參數會指定要設定哪些狀態位元，`nState` 參數則會包含那些位元的新值。 例如，下列範例會變更目前的父項目狀態 (所指定`hParentItem`) 中`CTreeCtrl`物件 (`m_treeCtrl`) 至**TVIS_EXPANDPARTIAL**:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#71](../mfc/codesnippet/cpp/tree-control-item-states-overview_1.cpp)]  
  
 變更狀態的另一個範例是設定項目的重疊影像。 若要達成此目的，`nStateMask`必須包含`TVIS_OVERLAYMASK`值，和`nState`必須包含 1 為基底的索引移位覆疊影像使用向左八個位元[INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408)巨集。 索引可為 0，表示不指定重疊影像。 將重疊影像必須已加入到覆疊影像的樹狀目錄控制項的清單由先前呼叫[cimagelist:: Setoverlayimage](../mfc/reference/cimagelist-class.md#setoverlayimage)函式。 函式指定 1 為基底的索引要加入的映像這是索引搭配**INDEXTOOVERLAYMASK**巨集。 樹狀目錄控制項有四個重疊影像。  
  
 若要設定項目的狀態影像，`nStateMask`必須包含`TVIS_STATEIMAGEMASK`值，和`nState`必須包含 1 為基底的索引移位狀態影像使用向左 12 個位元[INDEXTOSTATEIMAGEMASK](http://msdn.microsoft.com/library/windows/desktop/bb775597)巨集。 索引可為 0，表示不指定狀態影像。 如需重疊和狀態影像的詳細資訊，請參閱[樹狀目錄控制項影像清單](../mfc/tree-control-image-lists.md)。  
  
## <a name="see-also"></a>請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)

