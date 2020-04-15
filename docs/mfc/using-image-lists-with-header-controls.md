---
title: 搭配使用影像清單與標題控制項
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
ms.openlocfilehash: 8002c16d1cdf5e0683b642001409b6da9c260660
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366464"
---
# <a name="using-image-lists-with-header-controls"></a>搭配使用影像清單與標題控制項

標頭項能夠在標頭項中顯示圖像。 此圖像存儲在關聯的圖像清單中,為 16 x 16 圖元,其特徵與列表檢視控制項中使用的圖示圖像相同。 為了成功實現此行為,必須首先創建和初始化圖像清單,將列表與標頭控制項關聯,然後修改將顯示圖像的頭項的屬性。

以下過程說明瞭詳細資訊,使用指向標頭控制件`m_pHdrCtrl`( ) 的指標與指向影像清單的指標`m_pHdrImages`( ) 。

### <a name="to-display-an-image-in-a-header-item"></a>顯示標題項目中顯示影像

1. 使用[CImageList](../mfc/reference/cimagelist-class.md)建構函數建構新的影像清單(或使用現有影像清單物件),儲存產生的指標。

1. 通過調用[CImageList:::創建](../mfc/reference/cimagelist-class.md#create)來初始化新的圖像清單物件。 以下代碼是此調用的一個範例。

   [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]

1. 為每個標題項添加圖像。 以下代碼添加了兩個預定義的映射。

   [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]

1. 將映像清單與標頭控制項與對[CHeaderCtrl 的呼叫相關聯::SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist)。

1. 修改標題項以顯示關聯圖像清單中的圖像。 下面的範例將第一個影像(從`m_phdrImages`)分配給第一個標頭`m_pHdrCtrl`項目 。

   [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]

有關所用參數值的詳細資訊,請參閱相關的[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)。

> [!NOTE]
> 可以使用相同的圖像清單有多個控制項。 例如,在標準清單檢視控制項中,清單檢視控制項的小圖示檢視和清單檢視控制項的頭項都可以使用圖像清單(包含 16 x 16 像素圖像)。

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)
