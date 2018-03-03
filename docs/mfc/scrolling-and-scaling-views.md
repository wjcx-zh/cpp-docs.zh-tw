---
title: "捲動和縮放檢視 |Microsoft 文件"
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
- message handlers [MFC]
- scaling views [MFC]
- message handling [MFC], scroll bars in view class [MFC]
- scroll bars [MFC], messages
- scrolling views [MFC]
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8bd42a7da91f984c4cedc4deafc0ab9f4417495
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="scrolling-and-scaling-views"></a>捲動和縮放檢視
MFC 支援捲動和檢視，檢視會自動調整為其顯示在框架視窗的大小。 類別`CScrollView`支援這兩種檢視。  
  
 如需捲動和縮放比例的詳細資訊，請參閱類別[CScrollView](../mfc/reference/cscrollview-class.md)中*MFC 參考*。 如需捲動的範例，請參閱[Scribble 範例](../visual-cpp-samples.md)。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   捲動檢視  
  
-   縮放檢視  
  
-   [檢視座標](http://msdn.microsoft.com/library/windows/desktop/dd145205)  
  
##  <a name="_core_scrolling_a_view"></a>捲動檢視  
 經常文件大小大於其檢視可顯示的大小。 這可能是因為文件的資料會增加，或使用者縮小檢視的框架視窗。 在這種情況下，檢視必須支援捲動。  
  
 任何檢視可以處理中的捲軸訊息其`OnHScroll`和`OnVScroll`成員函式。 您可以在這些函式，其中一個實作捲軸訊息處理執行所有工作，或者您可以使用`CScrollView`類別來處理您的捲動。  
  
 `CScrollView` 會執行下列動作：  
  
-   管理視窗和檢視區大小和對應模式  
  
-   自動捲動以回應訊息捲軸  
  
 您可以指定多少捲動以檢視 「 頁面 」 （當使用者按一下捲軸中） 和"line"（當使用者按一下捲動箭號）。 規劃這些值以符合您檢視的性質。 例如，您可以捲動圖形檢視的 1 像素為單位，但根據行高文字文件中的增量。  
  
##  <a name="_core_scaling_a_view"></a>縮放檢視  
 當您想要自動調整其框架視窗的檢視時，您可以使用`CScrollView`調整規模，而不是捲動。 延展或縮小以配合視窗的工作區完全邏輯檢視。 已縮放的檢視有沒有捲軸。  
  
## <a name="see-also"></a>請參閱  
 [使用檢視](../mfc/using-views.md)

