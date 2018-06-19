---
title: 變更繪圖程式碼 (ATL 教學課程，第 4 部分) |Microsoft 文件
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c077aca8c3276fac963eda8cdd2c413a9d6d5f5b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358908"
---
# <a name="changing-the-drawing-code-atl-tutorial-part-4"></a>變更繪圖程式碼 (ATL 教學課程，第 4 部分)
根據預設，控制項的繪圖程式碼會顯示與文字**PolyCtl**。 在此步驟中，您將變更的程式碼，以顯示更有趣的東西。 涉及下列工作：  
  
-   修改標頭檔  
  
-   修改`OnDraw`函式  
  
-   將方法加入計算多邊形點數  
  
-   初始化的填滿色彩  
  
## <a name="modifying-the-header-file"></a>修改標頭檔  
 藉由新增數學函式支援啟動`sin`和`cos`，用來計算多邊形的點，並藉由建立陣列來儲存。  
  
#### <a name="to-modify-the-header-file"></a>若要修改的標頭檔  
  
1.  將行加入`#include <math.h>`PolyCtl.h 的頂端。 檔案最上方看起來應該像這樣：  
  
     [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]  
  
2.  一旦計算多邊形點，它們會儲存在類型的陣列`POINT`，因此之後的定義中加入陣列`m_nSides`PolyCtl.h 中：  
  
     [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_2.h)]  
  
## <a name="modifying-the-ondraw-method"></a>修改 OnDraw 方法  
 現在您應該修改`OnDraw`PolyCtl.h 中的方法。 您將加入的程式碼會建立新的畫筆和筆刷用來繪製您多邊形、，然後呼叫`Ellipse`和`Polygon`Win32 API 函式來執行實際的繪圖。  
  
#### <a name="to-modify-the-ondraw-function"></a>若要修改 OnDraw 函式  
  
1.  取代現有`OnDraw`PolyCtl.h 中以下列程式碼的方法：  
  
     [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]  
  
## <a name="adding-a-method-to-calculate-the-polygon-points"></a>將方法加入計算多邊形點數  
 加入方法，稱為`CalcPoints`，將會計算組成多邊形的外圍的點的座標。 這些計算會根據 RECT 變數傳遞至函式。  
  
#### <a name="to-add-the-calcpoints-method"></a>若要加入 CalcPoints 方法  
  
1.  新增的宣告`CalcPoints`至`IPolyCtl`公用區段`CPolyCtl`PolyCtl.h 中的類別：  
  
     [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_4.h)]  
  
     公用區段的最後一部分`CPolyCtl`類別看起來像這樣：  
  
     [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_5.h)]  
  
2.  加入這項實作`CalcPoints`PolyCtl.cpp 結尾的函式：  
  
     [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]  
  
## <a name="initializing-the-fill-color"></a>初始化的填滿色彩  
 初始化`m_clrFillColor`以預設的色彩。  
  
#### <a name="to-initialize-the-fill-color"></a>若要初始化的填滿色彩  
  
1.  做為綠色的預設色彩加入至這一行`CPolyCtl`PolyCtl.h 中的建構函式：  
  
     [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_7.h)]  
  
 建構函式現在看起來像這樣：  
  
 [!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_8.h)]  
  
## <a name="building-and-testing-the-control"></a>建置和測試控制項  
 重建控制項。 請確定它是否仍然開啟，請關閉 PolyCtl.htm 檔案，然後按一下**建置多邊形**上**建置**功能表。 您可以檢視控制項再次 PolyCtl.htm 頁面上，但這次使用 ActiveX 控制項測試容器。  
  
#### <a name="to-use-the-activex-control-test-container"></a>若要使用 ActiveX 控制項測試容器  
  
1.  建置和啟動 ActiveX 控制項測試容器。 如需詳細資訊，請參閱[TSTCON 範例： ActiveX 控制項測試容器](../visual-cpp-samples.md)。  
  
2.  測試容器中上**編輯**功能表上，按一下 **插入新控制項**。  
  
3.  找不到您的控制項，將呼叫`PolyCtl Class`，然後按一下**確定**。 您會看到一個圓圈中綠色的三角形。  
  
 請遵循下一個程序變更邊數。 若要修改測試容器中的雙重介面上的屬性，請使用**叫用方法**。  
  
#### <a name="to-modify-a-controls-property-from-within-the-test-container"></a>若要修改從內測試容器的控制項的屬性  
  
1.  在測試容器中，按一下 **叫用方法**上**控制項**功能表。  
  
     **叫用方法**對話方塊隨即出現。  
  
2.  選取**PropPut**版本**邊**屬性從**方法名稱**下拉式清單方塊。  
  
3.  型別`5`中**參數值**方塊中，按一下**設定值**，然後按一下**Invoke**。  
  
 請注意，此控制項不會變更。 雖然您邊數從內部變更設定`m_nSides`變數，這不會造成重新繪製控制項。 如果您切換至另一個應用程式，並再切換回測試容器，您會發現控制項已重新繪製，而且具有正確的側邊的數目。  
  
 若要修正這個問題，將呼叫加入`FireViewChange`函式，定義於`IViewObjectExImpl`之後設定邊數。 如果控制項在自己的視窗中，執行`FireViewChange`會呼叫`InvalidateRect`直接的方法。 如果控制項正在執行無視窗，`InvalidateRect`將容器的站台介面上呼叫方法。 這會強制重新繪製它自己的控制項。  
  
#### <a name="to-add-a-call-to-fireviewchange"></a>若要加入 FireViewChange 呼叫  
  
1.  加入呼叫以更新 PolyCtl.cpp`FireViewChange`至`put_Sides`方法。 當您完成時，`put_Sides`方法應該看起來像這樣：  
  
     [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]  
  
 在新增之後`FireViewChange`，重建並再試一次在 ActiveX 控制項測試容器中的控制項。 當您變更邊數，並按一下此時間`Invoke`，您應該會看到立即變更的控制項。  
  
 在下一個步驟中，您會加入事件。  
  
 [回到步驟 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; [至步驟 5](../atl/adding-an-event-atl-tutorial-part-5.md)  
  
## <a name="see-also"></a>另請參閱  
 [教學課程](../atl/active-template-library-atl-tutorial.md)   
 [使用測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md)

