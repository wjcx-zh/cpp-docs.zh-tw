---
title: "使用影像清單與標題控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a7a51aadc10a7722875597813e24ceb5960ab459
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-image-lists-with-header-controls"></a>搭配使用影像清單與標題控制項
標頭項目可以顯示的標題項目內的影像。 此映像，在相關聯的影像清單中，儲存為 16 x 16 像素，並有相同的特性清單檢視控制項中所使用的圖示影像。 若要成功實作這種行為，必須先建立和初始化映像清單、 將清單與標題控制項中，關聯，然後修改的屬性，將會顯示映像的標頭項目。  
  
 下列程序將說明的詳細資料，使用標題控制項的指標 (`m_pHdrCtrl`) 和影像清單的指標 (`m_pHdrImages`)。  
  
### <a name="to-display-an-image-in-a-header-item"></a>標頭項目中顯示影像  
  
1.  建構新的影像清單 （或使用現有的影像清單物件） 使用[CImageList](../mfc/reference/cimagelist-class.md)建構函式，儲存結果的指標。  
  
2.  初始化新的影像清單物件藉由呼叫[CImageList::Create](../mfc/reference/cimagelist-class.md#create)。 下列程式碼是此呼叫的範例。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]  
  
3.  將每個標頭項目的影像。 下列程式碼會加入兩個預先定義的映像。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]  
  
4.  影像清單與控制項產生關聯標頭呼叫[CHeaderCtrl::SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist)。  
  
5.  修改的標頭項目，以顯示相關聯的影像清單中的影像。 下列範例會從指派的第一個影像， `m_phdrImages`，第一個標頭項目中， `m_pHdrCtrl`。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]  
  
 如需所使用的參數值的詳細資訊，請參閱適當[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)。  
  
> [!NOTE]
>  很可能有多個使用相同的影像清單的控制項。 比方說，在標準清單檢視控制項，可能有清單檢視控制項的兩個小圖示檢視和清單檢視控制項的標題項目所使用影像清單 （的 16 x 16 像素的影像）。  
  
## <a name="see-also"></a>請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)

