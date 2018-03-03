---
title: "實作工作區域在清單控制項中的 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cefb8007fd9b73dda4c0e8a99e9ae9daa1bfcc34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-working-areas-in-list-controls"></a>在清單控制項中實作工作區域
根據預設，清單控制項排列標準格線樣式中的所有項目。 不過，另一個支援的方法，工作區的清單項目排列成矩形的群組。 實作工作區域的清單控制項的影像，請參閱 Windows SDK 中使用清單檢視控制項。  
  
> [!NOTE]
>  只有當清單控制項處於圖示或小圖示模式時，會顯示工作區。 不過，如果檢視切換到 報表 或 清單模式，仍會維護任何目前的工作區。  
  
 工作區可以用於顯示空的框線 （位於左側、 頂端及/或項目右邊），或導致時通常不會有一個要顯示水平捲軸。 另一個常見的用法是，建立多個工作區的項目可以移動或卸除。 使用此方法，您可以建立具有不同的意義在單一檢視中的區域。 使用者無法再將項目分類將它們放在不同的區域。 這個範例是具有讀取/寫入檔案的區域以及唯讀檔案的另一個區域的檔案系統的檢視。 如果檔案項目已移到唯讀區域中，它會自動變成唯讀。 將檔案從唯讀區域移到 [讀取/寫入] 區域會讓檔案讀取/寫入。  
  
 `CListCtrl`建立和管理您的清單控制項中的工作區域提供數個成員函式。 [GetWorkAreas](../mfc/reference/clistctrl-class.md#getworkareas)和[SetWorkAreas](../mfc/reference/clistctrl-class.md#setworkareas)擷取和設定的陣列`CRect`物件 (或`RECT`結構)，其中儲存您的清單控制項的目前實作的工作區域。 此外， [GetNumberOfWorkAreas](../mfc/reference/clistctrl-class.md#getnumberofworkareas)擷取清單控制項的工作區的目前數目 （根據預設，零）。  
  
## <a name="items-and-working-areas"></a>項目和工作區  
 建立工作區時，工作區域內的項目成為它的成員。 同樣地，如果項目移到工作區，它會成為它已移動的工作區域的成員。 如果項目不位於任何工作區，它會自動變成第一個 （索引 0） 工作區的成員。 如果您想要建立的項目，並讓它放置在特定的工作區域中，您必須建立項目，然後再將它移至所需的工作區，藉由呼叫[SetItemPosition](../mfc/reference/clistctrl-class.md#setitemposition)。 下列第二個範例會示範這項技術。  
  
 下列範例會實作四個工作區 (`rcWorkAreas`)，以 10 像素寬框線周圍每個工作區域，清單控制項中的相同大小的 (`m_WorkAreaListCtrl`)。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]  
  
 若要呼叫[ApproximateViewRect](../mfc/reference/clistctrl-class.md#approximateviewrect)進行，以取得整個區域顯示在一個區域中的所有項目所需的估計。 此預估值然後分成四個區域，並以 5 像素寬框線填補。  
  
 下一個範例會將現有的清單項目指派給每個群組 (`rcWorkAreas`)，並重新整理的控制項檢視 (`m_WorkAreaListCtrl`) 完成的效果。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]  
  
## <a name="see-also"></a>請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)

