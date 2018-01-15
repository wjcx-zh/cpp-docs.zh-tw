---
title: "索引標籤和索引標籤控制項屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- attributes [MFC], reference topics
- tab controls [MFC], attributes
- tabs [MFC]
- tabs [MFC], attributes
- CTabCtrl class [MFC], tab control attributes
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d10db5f1282c726b30536be35b348d50c8bb4a14
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tabs-and-tab-control-attributes"></a>索引標籤和索引標籤控制項屬性
您有相當大的控制權的外觀和行為的索引標籤控制項所組成的索引標籤 ([CTabCtrl](../mfc/reference/ctabctrl-class.md))。 每個索引標籤可以有標籤、 圖示、 項目狀態和與其相關聯的應用程式定義的 32 位元值。 對於每個索引標籤上，您可以顯示圖示、 標籤，或兩者。  
  
 此外，每個索引標籤項目可以有三種可能狀態： 已按下，未按下或反白顯示。 此狀態只可以設定來修改現有的索引標籤項目。 若要修改現有的索引標籤項目，擷取它呼叫[GetItem](../mfc/reference/ctabctrl-class.md#getitem)，修改`TCITEM`結構 (特別是**dwState**和**dwStateMask**資料成員)，然後傳回已修改`TCITEM`結構呼叫[SetItem](../mfc/reference/ctabctrl-class.md#setitem)。 如果您要清除所有索引標籤項目中的項目狀態`CTabCtrl`物件，呼叫以[DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall)。 此函式會重設 索引標籤的所有項目或所有項目，除了目前選取的狀態。  
  
 下列程式碼清除所有的索引標籤項目狀態，然後修改第三個項目的狀態：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]  
  
 如需索引標籤上屬性的詳細資訊，請參閱[索引標籤和索引標籤屬性](http://msdn.microsoft.com/library/windows/desktop/bb760550)Windows SDK 中。 如需將索引標籤加入索引標籤控制項的詳細資訊，請參閱[加入索引標籤，以索引標籤控制項](../mfc/adding-tabs-to-a-tab-control.md)本主題稍後。  
  
## <a name="see-also"></a>請參閱  
 [使用 CTabCtrl](../mfc/using-ctabctrl.md)   
 [控制項](../mfc/controls-mfc.md)

