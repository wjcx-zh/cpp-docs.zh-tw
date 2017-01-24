---
title: "清單項目和影像清單 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "CImageList 類別, 和清單項目"
  - "CListCtrl 類別, 影像清單"
  - "影像清單 [C++], 清單項目"
  - "清單項目, 影像清單"
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 清單項目和影像清單
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一個「項目」在清單控制項 \([CListCtrl](../mfc/reference/clistctrl-class.md)\) 包括圖示、標籤和可能其他資訊 \(「子項目」\)。  
  
 清單控制項項目的圖示會出現在影像清單中。  影像清單包含圖示檢視的大型圖示。  第二，選擇性，影像清單在控制項的其他檢視包含相同的圖示的小型版本可供使用。  第三個選擇性清單在某些檢視包含「狀態影像，例如核取方塊，以小圖示上顯示的。  第四個選擇性清單包含在清單控制項中的標頭項目中顯示的影像。  
  
> [!NOTE]
>  如果清單檢視控制項建立 `LVS_SHAREIMAGELISTS` 樣式，您要負責終結影像清單，並且不再使用時。  如果您指派相同的影像清單對多清單檢視控制項，請指定樣式;否則，多個控制項會終結相同的影像清單。  
  
 如需清單項目的詳細資訊，請參閱 [清單檢視影像清單](http://msdn.microsoft.com/library/windows/desktop/bb774736) 和 [項目和子項目](http://msdn.microsoft.com/library/windows/desktop/bb774736) 在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  請參閱《 *MFC 參考》中的*[CImageList](../mfc/reference/cimagelist-class.md) 和 [使用 CImageList](../mfc/using-cimagelist.md) 類別在文件這系列。  
  
 在插入新的項目至清單時，要建立清單控制項，您必須提供要用的影像清單。  下列範例示範這個程序中， `m_pImagelist` 是 `CImageList` 型別指標，而且 `m_listctrl` 為 `CListCtrl` 資料成員。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/CPP/list-items-and-image-lists_1.cpp)]  
  
 不過，因此，如果您不打算顯示在清單檢視或清單控制項的圖示，您不需要影像清單。  
  
## 請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)