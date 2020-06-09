---
title: 清單項目和影像清單
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
ms.openlocfilehash: 14abf72551d39b2d1b2069bd17da308b39d7f6cc
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621407"
---
# <a name="list-items-and-image-lists"></a>清單項目和影像清單

清單控制項（[CListCtrl](reference/clistctrl-class.md)）中的「專案」是由圖示、標籤和可能的其他資訊（在「子專案」中）所組成。

清單控制項項目的圖示會出現在影像清單中。 影像清單包含圖示檢視中使用的完整大小圖示。 第二個 (選擇性) 影像清單包含與在控制項的其他檢視中使用相同圖示的較小版本。 第三個選擇性清單包含「狀態」影像 (例如核取方塊)，用於在某些檢視中顯示於小圖示的前方。 第四個選擇性清單包含一些在清單控制項的個別標頭項目中顯示的影像。

> [!NOTE]
> 如果清單視圖控制項是使用 LVS_SHAREIMAGELISTS 樣式所建立，您就必須負責終結不再使用的影像清單。 如果您指派相同的影像清單給多個清單檢視控制項，請指定此樣式，否則可能出現多個控制項嘗試終結相同影像清單的情形。

如需有關清單專案的詳細資訊，請參閱 Windows SDK 中的[清單視圖影像清單](/windows/win32/Controls/using-list-view-controls)和[專案和子項](/windows/win32/Controls/using-list-view-controls)。 另請參閱*MFC 參考*中的類別[CImageList](reference/cimagelist-class.md)和在這一系列的文章中[使用 CImageList](using-cimagelist.md) 。

若要建立清單控制項，您必須在插入新的項目至清單時，提供要使用的影像清單。 下列範例會示範此程式，其中*m_pImagelist*是類型的指標 `CImageList` ，而*m_listctrl*是 `CListCtrl` 資料成員。

[!code-cpp[NVC_MFCControlLadenDialog#19](codesnippet/cpp/list-items-and-image-lists_1.cpp)]

不過，如果您不打算在清單檢視或清單控制項中顯示圖示，則不需要影像清單。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](using-clistctrl.md)<br/>
[控制項](controls-mfc.md)
