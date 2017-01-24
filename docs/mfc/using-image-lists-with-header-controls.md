---
title: "搭配使用影像清單與標題控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHeaderCtrl 類別, 影像清單"
  - "標題控制項, 影像清單"
  - "影像清單 [C++], 標題控制項"
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 搭配使用影像清單與標題控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

標題項目可以顯示在標題項目內的影像。  這個影像，儲存在一個關聯的影像清單，為 16 x 16 像素且具有相同圖示影像在清單檢視控制項使用的特性。  要成功實作這個行為，您必須先建立和初始化影像清單，使清單與標題控制項，然後修改要顯示影像標頭項目的屬性。  
  
 下列程序說明詳細資料，請使用指標標題控制項 \(`m_pHdrCtrl`\) 和指標影像清單 \(`m_pHdrImages`\)。  
  
### 顯示在標頭項目的影像。  
  
1.  建構新的影像清單 \(或使用現有的影像清單物件\) 使用 [CImageList](../mfc/reference/cimagelist-class.md) 建構函式，，儲存結果指標。  
  
2.  透過呼叫 [CImageList::Create](../Topic/CImageList::Create.md)初始化新的影像清單物件。  下列程式碼是這個呼叫的範例。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/CPP/using-image-lists-with-header-controls_1.cpp)]  
  
3.  將每個標題項目的影像。  下列程式碼加入兩個預先定義的影像。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/CPP/using-image-lists-with-header-controls_2.cpp)]  
  
4.  相關聯的影像清單與有標題控制項的 [CHeaderCtrl::SetImageList](../Topic/CHeaderCtrl::SetImageList.md)。  
  
5.  修改標頭項目中顯示從關聯的影像清單中的影像。  下列範例會將第一個影像，以 `m_phdrImages`，對第一個標頭項目，則為 `m_pHdrCtrl`。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/CPP/using-image-lists-with-header-controls_3.cpp)]  
  
 如需使用的參數值的詳細資訊，請參閱相關的 [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)。  
  
> [!NOTE]
>  有多個控制項使用同一個影像清單，則為。  例如，在標準清單檢視控制項，可能有清單檢視控制項的小圖示檢視和清單檢視控制項的標頭項目 \(16 個 x 16 個像素影像\) 使用的影像清單。  
  
## 請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)