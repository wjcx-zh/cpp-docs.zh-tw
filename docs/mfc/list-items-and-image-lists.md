---
title: 清單項目和影像清單
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
ms.openlocfilehash: cae387dc028df46a7891e68d49f5f0c5a89126c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571037"
---
# <a name="list-items-and-image-lists"></a>清單項目和影像清單

清單控制項中的"item"([CListCtrl](../mfc/reference/clistctrl-class.md)) 包含圖示、 標籤，以及可能是其他資訊 （「 子項目 」）。

清單控制項項目的圖示會出現在影像清單中。 影像清單包含圖示檢視中使用的完整大小圖示。 第二個 (選擇性) 影像清單包含與在控制項的其他檢視中使用相同圖示的較小版本。 第三個選擇性清單包含「狀態」影像 (例如核取方塊)，用於在某些檢視中顯示於小圖示的前方。 第四個選擇性清單包含一些在清單控制項的個別標頭項目中顯示的影像。

> [!NOTE]
>  如果 LVS_SHAREIMAGELISTS 樣式會建立清單檢視控制項，您必須負責終結影像清單，它們不會再使用時。 如果您指派相同的影像清單給多個清單檢視控制項，請指定此樣式，否則可能出現多個控制項嘗試終結相同影像清單的情形。

如需清單項目的詳細資訊，請參閱[清單檢視影像清單](/windows/desktop/Controls/using-list-view-controls)並[項目和子項目](/windows/desktop/Controls/using-list-view-controls)Windows SDK 中。 另請參閱類別[CImageList](../mfc/reference/cimagelist-class.md)中*MFC 參考 》* 並[使用 CImageList](../mfc/using-cimagelist.md)此系列文章中。

若要建立清單控制項，您必須在插入新的項目至清單時，提供要使用的影像清單。 下列範例示範此程序，其中*m_pImagelist*是類型的指標`CImageList`並*m_listctrl*是`CListCtrl`資料成員。

[!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]

不過，如果您不打算在清單檢視或清單控制項中顯示圖示，則不需要影像清單。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

