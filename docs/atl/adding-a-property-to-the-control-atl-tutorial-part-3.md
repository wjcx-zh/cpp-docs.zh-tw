---
title: 將屬性加入至控制項 (ATL 教學課程，第 3 部分)
ms.custom: get-started-article
ms.date: 09/26/2018
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
ms.openlocfilehash: 288dc9f5af57c02639d15a9a971419a633cfc08d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127583"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>將屬性加入至控制項 (ATL 教學課程，第 3 部分)

`IPolyCtl` 是包含控制項自訂方法和屬性的介面，您會在其中加入屬性。

### <a name="to-add-the-property-definitions-to-your-project"></a>將屬性定義加入至您的專案

1. 在**類別檢視**中，展開 [`Polygon`] 分支。

1. 以滑鼠右鍵按一下 [`IPolyCtl`]。

1. 在快捷方式功能表上，按一下 [**新增**]，然後按一下 [**加入屬性**]。 [**新增屬性**] wizard 隨即出現。

1. 輸入 `Sides` 做為**屬性名稱**。

1. 在 [**屬性類型**] 的下拉式清單中，選取 [`short`]。

1. 按一下 **[確定**] 以完成加入屬性。

1. 從**方案總管**，開啟多邊形 .idl，並取代 `IPolyCtl : IDispatch` 介面結尾的下列幾行：

    ```cpp
    short get_Sides();
    void set_Sides(short value);
    ```

    取代為

    ```cpp
    [propget, id(1), helpstring("property Sides")] HRESULT Sides([out, retval] short *pVal);
    [propput, id(1), helpstring("property Sides")] HRESULT Sides([in] short newVal);
    ```

1. 在**方案總管**中，開啟 PolyCtl，並在 `m_clrFillColor`定義之後加入下列幾行：

    [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]

雖然您現在有基本架構函式可設定和取出屬性，以及用來儲存屬性的變數，但您必須據以執行函式。

### <a name="to-update-the-get-and-put-methods"></a>若要更新 get 和 put 方法

1. 設定 `m_nSides`的預設值。 藉由在 PolyCtl 中將行新增至函式，讓預設圖形成為三角形：

    [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]

1. 執行 `Get` 和 `Put` 方法。 `get_Sides` 和 `put_Sides` 函式宣告已加入至 PolyCtl。 現在，將 `get_Sides` 和 `put_Sides` 的程式碼新增至 PolyCtl，如下所示：

    [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]

`get_Sides` 方法會透過 `pVal` 指標，傳回 `Sides` 屬性的目前值。 在 `put_Sides` 方法中，程式碼可確保使用者將 `Sides` 屬性設定為可接受的值。 最小值必須是3，而且因為每一端都會使用點陣列，100是最大值的合理限制。

您現在有一個名為 `Sides`的屬性。 在下一個步驟中，您將變更繪圖程式碼來使用它。

[回到步驟 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [的步驟 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)

## <a name="see-also"></a>另請參閱

[教學課程](../atl/active-template-library-atl-tutorial.md)
