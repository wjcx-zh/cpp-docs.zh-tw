---
title: 將在網頁上 (ATL 教學課程，第 7 部分) 控制項放 |Microsoft Docs
ms.custom: get-started-article
ms.date: 09/27/2018
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 052c6fa80b222a077fb41d861a4ea234f64073ec
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821604"
---
# <a name="putting-the-control-on-a-web-page-atl-tutorial-part-7"></a>將控制項放在網頁上 (ATL 教學課程，第 7 部分)

現在已完成您的控制項。 若要查看您在真實世界的情況下運作的控制項，請將它放在網頁上。 定義您的控制項時，所建立的 HTML 檔案，包含控制項。 開啟 PolyCtl.htm 檔案從**方案總管 中**，您可以看到您在網頁上的控制項。

在此步驟中，您將功能加入至控制項及指令碼來回應事件的網頁。 您也將修改要告知 Internet Explorer 的控制項是安全的指令碼的控制項。

## <a name="adding-new-functionality"></a>加入新的功能

### <a name="to-add-control-features"></a>若要將控制項新增功能

1. 開啟 PolyCtl.cpp，並取代下列程式碼：

    ```cpp
    if (PtInRegion(hRgn, xPos, yPos))
        Fire_ClickIn(xPos, yPos);
    else
        Fire_ClickOut(xPos, yPos);
    ```

    取代為

    ```cpp
    short temp = m_nSides;
    if (PtInRegion(hRgn, xPos, yPos))
    {
        Fire_ClickIn(xPos, yPos);
        put_Sides(++temp);
    }
    else
    {
        Fire_ClickOut(xPos, yPos);
        put_Sides(--temp);
    }
    ```

圖形現在將會新增或移除側邊，取決於您在其中按一下。

## <a name="scripting-the-web-page"></a>指令碼之 Web 網頁

控制項不會不執行任何動作的資訊，因此會變更網頁以回應您所傳送的事件。

### <a name="to-script-the-web-page"></a>若要編寫指令碼之 Web 網頁

1. 開啟 PolyCtl.htm 並選取 [HTML] 檢視。 將下列幾行新增至 HTML 程式碼中。 應該將它們加入後`</OBJECT>`之前`</BODY>`。

    ```html
    <SCRIPT LANGUAGE="VBScript">
    <!--
        Sub PolyCtl_ClickIn(x, y)
            MsgBox("Clicked (" & x & ", " & y & ") - adding side")
        End Sub
        Sub PolyCtl_ClickOut(x, y)
            MsgBox("Clicked (" & x & ", " & y & ") - removing side")
        End Sub
    -->
    </SCRIPT>
    ```

1. 儲存 HTM 檔案。

您已加入一些 VBScript 程式碼從控制項取得 Sides 屬性，如果您在控制項內按一下，邊數增加一。 如果您按一下控制項之外，您會減少一個邊數。

## <a name="indicating-that-the-control-is-safe-for-scripting"></a>表示控制項可安全用於指令碼

您可以檢視與控制項的網頁在 Internet Explorer 中，或者，更方便，使用 Visual c + + 內建網頁瀏覽器檢視。 若要查看您在 Web 瀏覽器檢視中的控制項，以滑鼠右鍵按一下 PolyCtl.htm，然後按一下**瀏覽器中的檢視**。

> [!NOTE]
> 如果看不到控制項，知道某些瀏覽器需要執行 ActiveX 控制項的設定調整。 請參閱有關如何啟用 ActiveX 控制項的瀏覽器的文件。

根據您目前的 Internet Explorer 安全性設定，您可能會收到安全性警示對話方塊，說明控制項可能不安全的指令碼，而且可能會造成損害。 例如，如果您的控制項顯示檔案，但也有`Delete`刪除某檔案的方法，則可放心如果只是在頁面上檢視。 它會是不安全地編寫指令碼，不過，因為有人可以呼叫`Delete`方法。

> [!IMPORTANT]
> 本教學課程中，您可以變更 Internet Explorer 執行未標示為安全的 ActiveX 控制項中的安全性設定。 在控制台中，按一下**網際網路內容**然後按一下**安全性**變更適當的設定。 當您完成本教學課程時，請回到其原始狀態變更安全性設定。

您可以以程式設計方式發出警示 Internet Explorer，它不需要顯示 [安全性警示] 對話方塊中，這個特定的控制項。 您可以使用`IObjectSafety`介面和 ATL 提供此介面的類別中實作[IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md)。 若要將介面新增至您的控制項，新增`IObjectSafetyImpl`至繼承的類別清單和加入其 COM 對應中的項目。

### <a name="to-add-iobjectsafetyimpl-to-the-control"></a>若要將 IObjectSafetyImpl 加入至控制項

1. 將下行加入至 PolyCtl.h 中繼承類別清單的結尾，並在上一行加入逗號：

    [!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]

1. 將下行新增至 PolyCtl.h 中的 COM 對應：

    [!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]

## <a name="building-and-testing-the-control"></a>建置和測試控制項

建置控制項。 一旦組建完成後，請再次瀏覽器檢視中開啟 PolyCtl.htm。 此時，網頁應該顯示直接不含**安全性警示** 對話方塊。 按一下內部多邊形;邊數增加一個。 按一下要減少的側邊的多邊形的外面。

[回到步驟 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="next-steps"></a>後續步驟

這總結 ATL 教學課程。 如需 ATL 詳細資訊的連結，請參閱 < [ATL 起始頁](../atl/active-template-library-atl-concepts.md)。

## <a name="see-also"></a>另請參閱

[教學課程](../atl/active-template-library-atl-tutorial.md)
