---
title: 使用工具列控制項中的映像清單 |Microsoft Docs
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
ms.openlocfilehash: c3604de0b3b24b638e549c6823ea6c95036543c1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401767"
---
# <a name="using-image-lists-in-a-toolbar-control"></a>在工具列控制項中使用影像清單

根據預設，在工具列控制項中的按鈕所使用的影像會儲存為單一的點陣圖。 不過，您也可以在一組映像清單中儲存按鈕的影像。 工具列控制項物件可以使用最多三個不同的映像清單：

- 啟用映像清單包含目前已啟用的工具列按鈕的影像。

- 停用映像清單包含目前已停用的工具列按鈕的影像。

- 反白顯示映像清單包含目前反白顯示的工具列按鈕的影像。 只有在工具列會使用 TBSTYLE_FLAT 樣式時，才使用此映像清單。

這些映像清單使用工具列控制項，當您建立關聯以`CToolBarCtrl`物件。 藉由呼叫來達成此種關聯[CToolBarCtrl::SetImageList](../mfc/reference/ctoolbarctrl-class.md#setimagelist)， [SetDisabledImageList](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist)，並[SetHotImageList](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist)。

根據預設，MFC 會使用`CToolBar`類別來實作 MFC 應用程式工具列。 不過，`GetToolBarCtrl`成員函式可以用來擷取內嵌`CToolBarCtrl`物件。 您接著可以呼叫`CToolBarCtrl`成員函式使用傳回的物件。

下列範例會示範這項技術，藉由指定啟用 (`m_ToolBarImages`) 和停用 (`m_ToolBarDisabledImages`) 的影像清單`CToolBarCtrl`物件 (`m_ToolBarCtrl`)。

[!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]

> [!NOTE]
>  工具列物件所使用的映像清單必須是永久物件。 基於這個理由，它們通常是資料成員的 MFC 類別;在此範例中，主框架視窗類別。

一旦影像清單相關聯`CToolBarCtrl`物件，此架構會自動顯示適當的按鈕影像。

## <a name="see-also"></a>另請參閱

[使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

