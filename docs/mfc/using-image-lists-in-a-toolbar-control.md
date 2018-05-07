---
title: 在工具列控制項中使用影像清單 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76325d2b078f51860cad7fa3fab61ed7c518a41c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-image-lists-in-a-toolbar-control"></a>在工具列控制項中使用影像清單
根據預設，在工具列控制項中的按鈕所使用的影像會儲存成單一的點陣圖。 不過，您也可以儲存按鈕影像的影像清單集合中。 工具列控制項物件可以使用最多三個不同的影像清單：  
  
-   啟用映像清單包含目前已啟用的工具列按鈕的影像。  
  
-   停用映像清單包含目前已停用的工具列按鈕的影像。  
  
-   反白顯示的影像清單包含目前反白顯示的工具列按鈕的影像。 工具列會使用時，才使用此映像清單**TBSTYLE_FLAT**樣式。  
  
 這些映像清單時，使用工具列控制項將它們與產生關聯`CToolBarCtrl`物件。 此關聯完成藉由呼叫[CToolBarCtrl::SetImageList](../mfc/reference/ctoolbarctrl-class.md#setimagelist)， [SetDisabledImageList](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist)，和[SetHotImageList](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist)。  
  
 根據預設，MFC 會使用`CToolBar`類別來實作 MFC 應用程式工具列。 不過，`GetToolBarCtrl`成員函式可以用來擷取內嵌`CToolBarCtrl`物件。 接著您可以呼叫`CToolBarCtrl`成員函式使用傳回的物件。  
  
 下列範例會示範這項技術，藉由指定啟用 (`m_ToolBarImages`) 和已停用 (`m_ToolBarDisabledImages`) 影像清單`CToolBarCtrl`物件 (`m_ToolBarCtrl`)。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]  
  
> [!NOTE]
>  使用工具列物件的影像清單必須是永久物件。 基於這個理由，它們通常是 MFC 類別; 事件類別資料成員在此範例中，主框架視窗類別。  
  
 一旦影像清單相關聯`CToolBarCtrl`物件時，架構會自動顯示適當的按鈕影像。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

