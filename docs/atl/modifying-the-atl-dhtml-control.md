---
title: 修改 ATL DHTML 控制項
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, modifying
- DHTML controls
- DHTML controls, modifying
ms.assetid: c053f35f-8629-4600-9595-721f5956777a
ms.openlocfilehash: 6c8976c013d0114a3115d3b0bc38fa4bc6acb5b7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275684"
---
# <a name="modifying-the-atl-dhtml-control"></a>修改 ATL DHTML 控制項

ATL 控制項精靈提供起始程式碼，讓您能夠建置和執行控制，因此您可以看到專案檔中寫入方法的方式，以及如何 DHTML 呼叫控制項的 c + + 程式碼，使用分派方法。 您可以新增任何分派方法的介面。 然後，您可以呼叫方法中的 HTML 資源。

## <a name="to-modify-the-atl-dhtml-control"></a>修改 ATL DHTML 控制項

1. 在 **類別檢視**，展開控制項專案。

   請注意，結束於 」 UI 」 中的介面的一種方法， `OnClick`。 結尾不是 「 UI 」 的介面並沒有任何方法。

1. Add 方法`MethodInvoked`結尾不是 「 UI。 」 的介面

   這個方法會加入至用於容器互動，而不使用 DHTML 與控制項互動的介面的控制項容器的介面。 只有容器可以叫用這個方法。

1. 在.cpp 檔案中尋找的截短方法，並新增程式碼，以顯示訊息方塊中，例如：

   [!code-cpp[NVC_ATL_COM#5](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_1.cpp)]

1. 新增另一個方法呼叫`HelloHTML`，只是這次將它新增至介面，結尾為"U"。 尋找虛設常式外`HelloHTML`方法中的.cpp 檔案，並新增程式碼，以顯示訊息方塊中，例如：

   [!code-cpp[NVC_ATL_COM#6](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_2.cpp)]

1. 新增第三個方法， `GoToURL`，結尾不是 「 UI。 」 的介面 實作這個方法，藉由呼叫[IWebBrowser2::Navigate](https://msdn.microsoft.com/library/aa752133.aspx)、，如下所示：

   [!code-cpp[NVC_ATL_COM#7](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_3.cpp)]

   您可以使用`IWebBrowser2`方法因為 ATL.h 檔案中為您提供該介面的指標。

接下來，修改 HTML 資源，來叫用您所建立的方法。 您將新增叫用這些方法的三個按鈕。

## <a name="to-modify-the-html-resource"></a>若要修改 HTML 資源

1. 在 [**方案總管] 中**，按兩下.htm 檔案，以顯示 HTML 資源。

   檢查在 HTML 中，特別是呼叫外部 Windows 分派方法。 HTML 呼叫的專案`OnClick`方法與參數指出此控制項的主體 (`theBody`) 和指派色彩 (「`red`")。 方法呼叫之後的文字會出現在按鈕的標籤。

1. 新增另一個`OnClick`方法，只會變更色彩。 例如: 

    ```html
    <br>
    <br>
    <BUTTON onclick='window.external.OnClick(theBody, "white");'>Refresh</BUTTON>
    ```

   這個方法會建立一個標示為的按鈕**重新整理**，使用者可以按一下以返回原始的白色背景的控制項。

1. 將呼叫加入`HelloHTML`您所建立的方法。 例如: 

    ```html
    <br>
    <br>
    <BUTTON onclick='window.external.HelloHTML();'>HelloHTML</BUTTON>
    ```

   這個方法會建立一個標示為的按鈕**HelloHTML**，使用者可以按一下以顯示`HelloHTML`訊息方塊。

您現在可以建置並[測試修改過的 DHTML 控制項](../atl/testing-the-modified-atl-dhtml-control.md)。

## <a name="see-also"></a>另請參閱

[DHTML 控制項的支援](../atl/atl-support-for-dhtml-controls.md)
