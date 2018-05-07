---
title: 標題控制項和清單控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], with CHeaderCtrl
- CListCtrl class [MFC], header controls
- CHeaderCtrl class [MFC], with CListCtrl
- controls [MFC], header
- header controls [MFC]
- header controls [MFC], list controls used with
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a84386781bf28edb9223f608fa7a64040eb68379
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="header-control-and-list-control"></a>標題控制項和清單控制項
在大部分情況下，您將使用內嵌在此標題控制項[CListCtrl](../mfc/reference/clistctrl-class.md)或[CListView](../mfc/reference/clistview-class.md)物件。 不過，有個別的標頭控制項物件需要這樣做，例如操作資料、 排列在資料行或資料列中的情況[CView](../mfc/reference/cview-class.md)-衍生物件。 在這些情況下，您需要進一步控制的外觀和內嵌的標題控制項的預設行為。  
  
 您想要提供標準標頭控制項的一般情況下，預設行為，您可能想要使用[CListCtrl](../mfc/reference/clistctrl-class.md)或[CListView](../mfc/reference/clistview-class.md)改為。 使用`CListCtrl`當您想要內嵌在清單檢視通用控制項的預設標題控制項的功能。 使用[CListView](../mfc/reference/clistview-class.md)當您想要檢視物件中內嵌的預設標題控制項的功能。  
  
> [!NOTE]
>  這些控制項只包含內建的標頭控制，如果清單檢視控制項使用建立`LVS_REPORT`樣式。  
  
 在大部分情況下，變更包含清單檢視控制項的樣式可修改內嵌的標題控制項的外觀。 此外，透過父清單檢視控制項的成員函式可以取得標頭控制項的相關資訊。 不過，完整的控制權，並存取，屬性和內嵌的標題控制項的樣式，建議您使用取得標頭控制物件的指標。  
  
 內嵌的標題控制項物件可從**CListCtrl**或`CListView`個別的類別呼叫`GetHeaderCtrl`成員函式。 下列程式碼示範：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/cpp/header-control-and-list-control_1.cpp)]  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [使用影像清單與標題控制項](../mfc/using-image-lists-with-header-controls.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控制項](../mfc/controls-mfc.md)

