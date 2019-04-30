---
title: 搭配使用影像清單與標題控制項
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
ms.openlocfilehash: 3d9a4a0c655fa46c15d8c4d9b2b4e90cd34c2937
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411535"
---
# <a name="using-image-lists-with-header-controls"></a>搭配使用影像清單與標題控制項

標頭項目能夠顯示的標題項目內的影像。 此映像，在相關聯的映像清單中，儲存為 16 x 16 像素，並具有相同特性做為清單檢視控制項中所使用的圖示影像。 若要成功地實作這種行為，必須先建立和初始化映像清單、 將此清單與標題控制項，並在控制項，再修改標題項目將會顯示映像的屬性。

下列程序說明的詳細資訊，請使用標題控制項的指標 (`m_pHdrCtrl`) 和影像清單的指標 (`m_pHdrImages`)。

### <a name="to-display-an-image-in-a-header-item"></a>標頭項目中顯示影像

1. 建構新的影像清單 （或使用現有的影像清單物件） 使用[CImageList](../mfc/reference/cimagelist-class.md)建構函式，儲存結果的指標。

1. 藉由呼叫初始化新的影像清單物件[CImageList::Create](../mfc/reference/cimagelist-class.md#create)。 下列程式碼是此呼叫的其中一個範例。

   [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]

1. 將每個標頭項目的影像。 下列程式碼會新增兩個預先定義的映像。

   [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]

1. 影像清單與控制項相關聯標頭呼叫[CHeaderCtrl::SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist)。

1. 修改標頭項目，以顯示相關聯的映像清單中的影像。 下列範例會從第一個映像中，指派`m_phdrImages`，第一個標頭項目， `m_pHdrCtrl`。

   [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]

如需使用的參數值的詳細資訊，請參閱相關[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)。

> [!NOTE]
>  可以有多個使用相同的映像清單的控制項。 比方說，在標準的清單檢視控制項中，可能有這兩個小圖示檢視的清單檢視控制項和清單檢視控制項的標題項目所使用的映像清單 （的 16 x 16 像素的影像）。

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)
