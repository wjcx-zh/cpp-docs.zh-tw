---
title: 變更繪圖程式碼 (ATL 教學課程，第 4 部分)
ms.custom: get-started-article
ms.date: 09/26/2018
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
ms.openlocfilehash: 319a27b55c394349de751546457b0741c0799cfc
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167639"
---
# <a name="changing-the-drawing-code-atl-tutorial-part-4"></a>變更繪圖程式碼 (ATL 教學課程，第 4 部分)

根據預設，控制項的繪製程式碼會顯示正方形和文字**PolyCtl**。 在此步驟中，您將變更程式碼，以顯示更有趣的內容。 涉及下列工作：

- 修改標頭檔

- `OnDraw`修改函式

- 新增方法來計算多邊形點

- 初始化填滿色彩

## <a name="modifying-the-header-file"></a>修改標頭檔

首先，新增對 math 函數`sin`和`cos`的支援，這將會用來計算多邊形點，並藉由建立陣列來儲存位置。

### <a name="to-modify-the-header-file"></a>修改標頭檔

1. 將行`#include <math.h>`新增至 PolyCtl 的頂端。 檔案頂端看起來應該像這樣：

    [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]

1. 藉由`IProvideClassInfo`將下列程式碼新增至 PolyCtl，來執行介面來提供控制項的方法資訊。 在類別`CPolyCtl`中，將行取代為：

    ```cpp
    public CComControl<CPolyCtl>
    ```

    取代為

    ```cpp
    public CComControl<CPolyCtl>,
    public IProvideClassInfo2Impl<&CLSID_PolyCtl, &DIID__IPolyCtlEvents, &LIBID_PolygonLib>
    ```

    在中`BEGIN_COM_MAP(CPolyCtl)`，新增下列幾行：

    ```cpp
    COM_INTERFACE_ENTRY(IProvideClassInfo)
    COM_INTERFACE_ENTRY(IProvideClassInfo2)
    ```

1. 一旦計算多邊形點之後，它們就會儲存在型`POINT`別的陣列中，因此，請在 PolyCtl 中的定義`short m_nSides;`語句後面加入陣列：

    [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_2.h)]

## <a name="modifying-the-ondraw-method"></a>修改 OnDraw 方法

現在您應該修改 PolyCtl `OnDraw`中的方法。 您將加入的程式碼會建立用來繪製多邊形的新畫筆和筆刷，然後呼叫`Ellipse`和`Polygon` WIN32 API 函式來執行實際繪圖。

### <a name="to-modify-the-ondraw-function"></a>若要修改 OnDraw 函數

1. 使用下列程式`OnDraw`代碼取代 PolyCtl 中的現有方法：

    [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]

## <a name="adding-a-method-to-calculate-the-polygon-points"></a>新增方法來計算多邊形點

新增名`CalcPoints`為的方法，其會計算構成多邊形周長之點的座標。 這些計算將以傳遞至函式的 RECT 變數為基礎。

### <a name="to-add-the-calcpoints-method"></a>若要新增 CalcPoints 方法

1. 在 PolyCtl 中， `CalcPoints`將的`IPolyCtl`宣告新增至`CPolyCtl`類別的 public 區段：

    [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_4.h)]

    `CPolyCtl`類別之公用區段的最後部分如下所示：

    [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_5.h)]

1. 將此函式的`CalcPoints`執行方式新增至 PolyCtl 的結尾：

    [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]

## <a name="initializing-the-fill-color"></a>初始化填滿色彩

使用`m_clrFillColor`預設色彩進行初始化。

### <a name="to-initialize-the-fill-color"></a>若要初始化填滿色彩

1. 將下面這一行新增至 PolyCtl 中的`CPolyCtl`函式，以使用綠色作為預設色彩：

    [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_7.h)]

此函式現在看起來像這樣：

[!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_8.h)]

## <a name="building-and-testing-the-control"></a>建置和測試控制項

重建控制項。 如果 PolyCtl 的 .htm 檔案仍為開啟狀態，請確定該檔案已關閉，然後按一下 [**建立**] 功能表上的 [**建立多邊形**]。 您可以從 [PolyCtl] 頁面再次查看控制項，但這次使用 ActiveX 控制項測試容器。

### <a name="to-use-the-activex-control-test-container"></a>若要使用 ActiveX 控制項測試容器

1. 建立並啟動 ActiveX 控制項測試容器。 您可以在 GitHub 上找到[TSTCON 範例： ActiveX 控制項測試容器](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole/TstCon)。

    > [!NOTE]
    > 對於`ATL::CW2AEX`涉及的錯誤，請在腳本 .cpp 中， `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT );`將`TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT.m_psz );`行取代為`TRACE( "Source Text: %s\n", COLE2CT( bstrSourceLineText ) );` ， `TRACE( "Source Text: %s\n", bstrSourceLineText );`並使用行。<br/>
    > 對於涉及`HMONITOR`的錯誤，請在`TCProps`專案中開啟 stdafx.h，並取代：
    >
    > ```cpp
    > #ifndef WINVER
    > #define WINVER 0x0400
    > #endif
    > ```
    >
    > 取代為
    >
    > ```cpp
    > #ifndef WINVER
    > #define WINVER 0x0500
    > #define _WIN32_WINNT 0x0500
    > #endif
    > ```

1. 在 [**測試容器**] 的 [**編輯**] 功能表上，按一下 [**插入新控制項**]。

1. 找出您的控制項，這將`PolyCtl class`被呼叫，然後按一下 **[確定]**。 您會在圓形內看到綠色三角形。

請嘗試遵循下一個程式來變更側邊數目。 若要從**測試容器**中修改雙重介面的屬性，請使用**Invoke 方法**。

### <a name="to-modify-a-controls-property-from-within-the-test-container"></a>若要從測試容器內修改控制項的屬性

1. 在 [**測試容器**] 中，按一下 [**控制項**] 功能表上的 [叫用**方法**]。

    [叫用**方法**] 對話方塊隨即顯示。

1. 從 [**方法名稱**] 下拉式清單方塊中選取 [**側邊**] 屬性的 [ **PropPut**版本]。

1. 在`5` [**參數值**] 方塊中輸入 **，按一下 [****設定值**]，然後按一下 [叫用]。

請注意，此控制項不會變更。 雖然您會藉由設定`m_nSides`變數在內部變更邊的數目，但這並不會造成重新繪製控制項。 如果您切換至另一個應用程式，然後切換回**測試容器**，您會發現控制項已重新繪製，而且有正確的邊數目。

若要更正此問題，請在您設定`FireViewChange`的端數之後`IViewObjectExImpl`，新增對函式的呼叫（定義于中）。 如果控制項在自己的視窗中執行， `FireViewChange`則會直接呼叫`InvalidateRect`方法。 如果控制項是以無視窗執行， `InvalidateRect`則會在容器的網站介面上呼叫方法。 這會強制控制項自行重新繪製。

### <a name="to-add-a-call-to-fireviewchange"></a>若要新增對 FireViewChange 的呼叫

1. 藉由將對的呼叫新增`FireViewChange`至`put_Sides`方法，以更新 PolyCtl。 當您完成時，此`put_Sides`方法看起來應該像這樣：

    [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]

新增`FireViewChange`之後，請重建，並在 ActiveX 控制項測試容器中再次嘗試該控制項。 這次當您變更側邊數目並按一下`Invoke`時，您應該會立即看到控制項變更。

在下一個步驟中，您將新增事件。

[回到步驟 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124;[至步驟 5](../atl/adding-an-event-atl-tutorial-part-5.md)

## <a name="see-also"></a>另請參閱

[教學課程](../atl/active-template-library-atl-tutorial.md)<br/>
[使用測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md)
