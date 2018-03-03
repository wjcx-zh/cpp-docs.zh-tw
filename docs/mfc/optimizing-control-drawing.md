---
title: "最佳化控制項繪圖 |Microsoft 文件"
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
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 29ff985d-9bf5-4678-b62d-aad12def75fb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b3e79a7b8e539198844c106a9c41408f04d69186
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="optimizing-control-drawing"></a>最佳化控制項繪圖
當指示控制項將其本身拉入到容器提供的裝置內容中時，它通常會選取 GDI 物件 (例如畫筆、筆刷和字型) 到裝置內容中，執行其繪製作業，然後還原先前的 GDI 物件。 如果容器具有要引入的多個控制項相同的裝置內容，因此它需要的每個控制項選取 GDI 物件則可以儲存如果控制項不會個別還原先前選取的物件。 在拉入所有的控制項之後，容器就可以自動還原原始物件。  
  
 若要偵測容器是否支援這項技巧，控制項可呼叫[colecontrol:: Isoptimizeddraw](../mfc/reference/colecontrol-class.md#isoptimizeddraw)成員函式。 如果此函數會傳回**TRUE**，控制項可以略過正常步驟，還原先前選取的物件。  
  
 考慮具有以下 (未最佳化的) `OnDraw` 函式的控制項：  
  
 [!code-cpp[NVC_MFC_AxOpt#15](../mfc/codesnippet/cpp/optimizing-control-drawing_1.cpp)]  
  
 在此範例中，畫筆和筆刷為區域變數，表示當其超出範圍 (`OnDraw` 函式結束時) 時會呼叫其解構函式。 解構函式會嘗試刪除對應的 GDI 物件。 但是，如果您打算在從 `OnDraw` 傳回時讓它們保持選入裝置內容中，就不應該予以刪除。  
  
 若要避免[CPen](../mfc/reference/cpen-class.md)和[CBrush](../mfc/reference/cbrush-class.md)物件被終結時`OnDraw`完成時，將它們儲存在成員變數，而非區域變數。 在控制項的類別宣告中，加入兩個新成員變數的宣告：  
  
 [!code-cpp[NVC_MFC_AxOpt#16](../mfc/codesnippet/cpp/optimizing-control-drawing_2.h)]  
[!code-cpp[NVC_MFC_AxOpt#17](../mfc/codesnippet/cpp/optimizing-control-drawing_3.h)]  
  
 然後，就可以如下所示重寫 `OnDraw` 函式:  
  
 [!code-cpp[NVC_MFC_AxOpt#18](../mfc/codesnippet/cpp/optimizing-control-drawing_4.cpp)]  
  
 這個方法可以避免每次呼叫 `OnDraw` 時建立畫筆和筆刷。 速度的提升則會以維護其他執行個體資料的成本為代價。  
  
 如果 ForeColor 或 BackColor 屬性變更時，就需要再次建立畫筆或筆刷。 若要這樣做，請覆寫[OnForeColorChanged](../mfc/reference/colecontrol-class.md#onforecolorchanged)和[OnBackColorChanged](../mfc/reference/colecontrol-class.md#onbackcolorchanged)成員函式：  
  
 [!code-cpp[NVC_MFC_AxOpt#19](../mfc/codesnippet/cpp/optimizing-control-drawing_5.cpp)]  
  
 最後，為排除不必要的 `SelectObject` 呼叫，請如下所示修改 `OnDraw`：  
  
 [!code-cpp[NVC_MFC_AxOpt#20](../mfc/codesnippet/cpp/optimizing-control-drawing_6.cpp)]  
  
## <a name="see-also"></a>請參閱  
 [MFC ActiveX 控制項： 最佳化](../mfc/mfc-activex-controls-optimization.md)   
 [COleControl 類別](../mfc/reference/colecontrol-class.md)   
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)   
 [MFC ActiveX 控制項：繪製 ActiveX 控制項](../mfc/mfc-activex-controls-painting-an-activex-control.md)

