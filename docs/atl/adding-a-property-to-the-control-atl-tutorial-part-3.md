---
title: 將屬性加入至控制項 (ATL 教學課程，第 3 部分)
ms.custom: get-started-article
ms.date: 09/26/2018
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
ms.openlocfilehash: b5f9f9c8fde44dd67a9a05aeae0f91fb7b5f2f4d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252602"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>將屬性加入至控制項 (ATL 教學課程，第 3 部分)

`IPolyCtl` 是包含控制項的自訂方法和屬性的介面，您會將屬性加入它。

### <a name="to-add-the-property-definitions-to-your-project"></a>若要將屬性定義加入至專案

1. 在 **類別檢視**，展開 `Polygon`分支。

1. 以滑鼠右鍵按一下`IPolyCtl`。

1. 在捷徑功能表，按一下 **新增**，然後按一下**加入屬性**。 **加入屬性**精靈 隨即出現。

1. 型別`Sides`作為**的屬性名稱**。

1. 在下拉式清單中**屬性的型別**，選取`short`。

1. 按一下 **確定**以完成新增屬性。

1. 從**方案總管**，開啟 Polygon.idl，並取代下列幾行的結尾`IPolyCtl : IDispatch`介面：

    ```cpp
    short get_Sides();
    void set_Sides(short value);
    ```

    取代為

    ```cpp
    [propget, id(1), helpstring("property Sides")] HRESULT Sides([out, retval] short *pVal);
    [propput, id(1), helpstring("property Sides")] HRESULT Sides([in] short newVal);
    ```

1. 從**方案總管**，開啟 PolyCtl.h，並新增下列幾行的定義之後`m_clrFillColor`:

    [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]

雖然您現在有基本架構的函式，來設定和擷取屬性和變數來儲存此屬性，您必須據此實作的函式。

### <a name="to-update-the-get-and-put-methods"></a>若要更新的 get 和 put 方法

1. 設定的預設值`m_nSides`。 請將這一行新增至 PolyCtl.h 中建構函式圖形三角形的預設值：

    [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]

1. 實作`Get`和`Put`方法。 `get_Sides`和`put_Sides`函式宣告已加入至 PolyCtl.h。 現在將新增的程式碼`get_Sides`和`put_Sides`至 PolyCtl.cpp 取代下列項目：

    [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]

`get_Sides`方法會傳回目前的值`Sides`透過屬性`pVal`指標。 在 `put_Sides`方法，將程式碼可確保在設定使用者`Sides`屬性設為可接受的值。 最小值必須是 3，而且因為資料點的陣列將會用於每一端，100 合理的限制，最大值。

您現在有一個稱為屬性`Sides`。 在下一個步驟中，您會變更繪圖程式碼來使用它。

[回到步驟 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [至步驟 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)

## <a name="see-also"></a>另請參閱

[教學課程](../atl/active-template-library-atl-tutorial.md)
