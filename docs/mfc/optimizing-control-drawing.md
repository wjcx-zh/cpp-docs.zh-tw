---
title: "最佳化控制項繪圖 | Microsoft Docs"
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
  - "MFC ActiveX 控制項, 最佳化"
ms.assetid: 29ff985d-9bf5-4678-b62d-aad12def75fb
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 最佳化控制項繪圖
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當控制項表示會引入一由容器提供的裝置內容時，它通常會選取 GDI 物件 \(例如畫筆、筆刷和字型\) 到裝置內容中，會繪製作業，還原先前 GDI 的物件。  如果容器有要引入的多個控制項相同的裝置內容，因此它需要的每個控制項選取 GDI 物件則可以儲存如果控制項不會個別還原先前選取的物件。  在所有控制項繪製之後，容器可以自動還原原始物件。  
  
 若要偵測容器是否支援這個方法之後，控制項會呼叫 [COleControl::IsOptimizedDraw](../Topic/COleControl::IsOptimizedDraw.md) 成員函式。  如果這個函式會傳回 **TRUE**，控制項可以略過正常步驟還原先前選取的物件。  
  
 假設有以下的控制項 \( `OnDraw` \) 未最佳化的函式:  
  
 [!code-cpp[NVC_MFC_AxOpt#15](../mfc/codesnippet/CPP/optimizing-control-drawing_1.cpp)]  
  
 畫筆和筆刷在本例中為區域變數，表示其解構函式會呼叫，以便在超出範圍時 \(在 `OnDraw` 函式結束時\)。  解構函式會嘗試刪除對應的 GDI 物件。  它們，如果您打算讓它們被選取到裝置內容中傳回的值，則為 `OnDraw`，但不應該刪除。  
  
 若要防止 [CPen](../mfc/reference/cpen-class.md) 和 [CBrush](../mfc/reference/cbrush-class.md) 物件被終結，當 `OnDraw` 完成時，請將其儲存在成員變數而非區域變數。  在控制項的類別宣告，請加入兩個新的成員變數的宣告:  
  
 [!code-cpp[NVC_MFC_AxOpt#16](../mfc/codesnippet/CPP/optimizing-control-drawing_2.h)]  
[!code-cpp[NVC_MFC_AxOpt#17](../mfc/codesnippet/CPP/optimizing-control-drawing_3.h)]  
  
 然後就可以呼叫 `OnDraw`方法，如下所示:  
  
 [!code-cpp[NVC_MFC_AxOpt#18](../mfc/codesnippet/CPP/optimizing-control-drawing_4.cpp)]  
  
 `OnDraw` ，在呼叫時，這個方法可以避免這個畫筆和筆刷的建立。  速度來改善以維護不同的執行個體資料為代價。  
  
 如果控制項或背景色彩屬性變更時，這個筆刷或需要重新建立。  若要這麼做，請覆寫 [OnForeColorChanged](../Topic/COleControl::OnForeColorChanged.md) 和 [OnBackColorChanged](../Topic/COleControl::OnBackColorChanged.md) 成員函式:  
  
 [!code-cpp[NVC_MFC_AxOpt#19](../mfc/codesnippet/CPP/optimizing-control-drawing_5.cpp)]  
  
 最後，排除不必要的呼叫 `SelectObject` ，請修改 `OnDraw` 如下:  
  
 [!code-cpp[NVC_MFC_AxOpt#20](../mfc/codesnippet/CPP/optimizing-control-drawing_6.cpp)]  
  
## 請參閱  
 [MFC ActiveX 控制項：最佳化](../mfc/mfc-activex-controls-optimization.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)   
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)   
 [MFC ActiveX 控制項：繪製 ActiveX 控制項](../mfc/mfc-activex-controls-painting-an-activex-control.md)