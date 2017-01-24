---
title: "變更繪圖程式碼 (ATL 教學課程，第 4 部分) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ATL_MIN_CRT 巨集"
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
caps.latest.revision: 18
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 變更繪圖程式碼 (ATL 教學課程，第 4 部分)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根據預設，控制項的繪圖程式碼顯示方形和文字 **PolyCtl**。  在這個步驟中，您會變更程式碼顯示更多的事情。  是包含下列工作的:  
  
-   修改標頭檔  
  
-   修改 `OnDraw` 函式  
  
-   將方法計算多邊形點  
  
-   初始化填滿色彩  
  
## 修改標頭檔  
 藉由加入支援開始數學函式 `sin` 和 `cos`，將使用的建立陣列儲存位置計算多邊形、，和。  
  
#### 修改標頭檔  
  
1.  將線條 `#include _<math.h_>` 至 PolyCtl.h 頂端。  在檔案頂端看起來應該如下所示:  
  
     [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]  
  
2.  一旦多邊形的計算，則會在陣列中儲存型別 `POINT`，所以，請在 `m_nSides` 的定義之後。PolyCtl.h 的將陣列:  
  
     [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_2.h)]  
  
## 修改 OnDraw 方法  
 現在您應該修改在 PolyCtl.h 的 `OnDraw` 方法。  程式碼將建立自己的繪製多邊形，然後呼叫 `Ellipse` 和 `Polygon` Win32 API 函式來執行實際繪製的新筆刷的畫筆和筆刷。  
  
#### 修改 OnDraw 函式  
  
1.  使用下列程式碼取代 PolyCtl.h 的現有 `OnDraw` 方法:  
  
     [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]  
  
## 將方法計算多邊形點  
 加入方法，呼叫 `CalcPoints`，會計算點座標組成周邊多邊形。  這些計算視傳遞至函式的變數。  
  
#### 將 CalcPoints 方法  
  
1.  將的宣告變更 `CalcPoints``CPolyCtl` 類別的 `IPolyCtl` 公開部分在 PolyCtl.h 的:  
  
     [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_4.h)]  
  
     `CPolyCtl` 類別的 public 區段的最後一部分如下所示:  
  
     [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_5.h)]  
  
2.  將 `CalcPoints` 函式的實作加入至 PolyCtl.cpp 的結尾:  
  
     [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]  
  
## 初始化填滿色彩  
 使用預設色彩的 `m_clrFillColor` 。  
  
#### 初始化填滿色彩  
  
1.  使用綠色，則預設色彩將這一行程式碼加入至 PolyCtl.h 的 `CPolyCtl` 建構函式:  
  
     [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_7.h)]  
  
 建構函式現在看起來就像這樣:  
  
 [!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_8.h)]  
  
## 建置和測試控制項  
 重新建置控制項。  判斷 PolyCtl.htm 檔案中 \[**建置**\] 功能表關閉，若已開啟，然後按一下 \[**建立多邊形**\] 。  您可以再次檢視控制項從 PolyCtl.htm 網頁，不過，這次使用 ActiveX 控制項測試容器。  
  
#### 使用 ActiveX 控制項測試容器  
  
1.  建置並啟動 ActiveX 控制項測試容器。  如需詳細資訊，請參閱 [TSTCON 範例:ActiveX 控制項測試容器](../top/visual-cpp-samples.md)。  
  
2.  在測試容器，請在 \[**編輯**\] 功能表上，按一下 \[**插入新的控制項**\]。  
  
3.  找出控制項，會呼叫 `PolyCtl Class`並按一下 \[**確定**\]。  您會在圓圈中有一個綠色三角形。  
  
 嘗試變更邊數依照下一個程序。  若要修改在雙重介面的屬性從測試容器的內部，請使用 **Invoke Methods**。  
  
#### 修改控制項的屬性從測試容器內  
  
1.  在測試容器，請按一下 \[**叫用方法**\] 在 \[**控制**\] 功能表。  
  
     \[**叫用方法**\] 對話方塊隨即顯示。  
  
2.  選取 **Sides** 屬性的 **PropPut** 版本從 \[**方法名稱**\] 下拉式清單方塊。  
  
3.  在  方塊中輸入 \[**參數值**\] 的 `5` \[**設定值**\]，按一下 ，然後按一下 \[**叫用**\]。  
  
 請注意控制項並不會變更。  雖然您可以設定 `m_nSides` 變數內部變更的邊數，這不會導致控制項重新繪製。  如果您切換至其他應用程式再切換回測試容器，您會發現控制項重新繪製了其中的正確數目的。  
  
 若要修正這個問題，請將呼叫加入至 `FireViewChange` 函式，定義在 `IViewObjectExImpl`，因此，在設定之後的數目。  如果控制項在其視窗內執行， `FireViewChange` 會直接呼叫 `InvalidateRect` 方法。  如果控制項是無視窗 `InvalidateRect` 執行，則將呼叫容器的位置介面。  這會強制控制項重新自我繪製。  
  
#### 將呼叫加入至 FireViewChange  
  
1.  藉由將呼叫加入至 PolyCtl.cpp 更新 `FireViewChange``put_Sides` 方法。  當您完成時， `put_Sides` 方法看起來應該如下所示:  
  
     [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]  
  
 在加入 `FireViewChange`之後，重新建置並再試一次控制項在 ActiveX 控制項測試容器。  這次，當您變更邊數並按一下 `Invoke`時，應該立即看到控制項的變更。  
  
 在下一個步驟中，您會將事件。  
  
 [回到步驟 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; [在 &#91;步驟 5](../atl/adding-an-event-atl-tutorial-part-5.md)  
  
## 請參閱  
 [教學課程](../atl/active-template-library-atl-tutorial.md)   
 [使用測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md)