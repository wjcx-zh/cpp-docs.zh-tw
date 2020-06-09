---
title: ActiveX 控制項容器：在非對話方塊容器中使用控制項
ms.date: 11/04/2016
helpviewer_keywords:
- Create method [MFC], ActiveX controls
- CreateControl method [MFC]
- ActiveX controls [MFC], creating
- ActiveX control containers [MFC], non-dialog containers
- ActiveX control containers [MFC], inserting controls
ms.assetid: 46f195b0-b8ca-4409-8cca-fbfaf2c9ab9f
ms.openlocfilehash: b010c35f32462810cbdb008e5688d4b41254fad1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620766"
---
# <a name="activex-control-containers-using-controls-in-a-non-dialog-container"></a>ActiveX 控制項容器：在非對話方塊容器中使用控制項

在某些應用程式 (例如 SDI 或 MDI 應用程式) 中，您會想要在應用程式的視窗中內嵌控制項。 包裝函式類別的**Create**成員函式（由 Visual C++ 插入）可以動態建立控制項的實例，而不需要對話方塊。

**Create**成員函式具有下列參數：

*lpszWindowName*<br/>
要在控制項的 Text 或 Caption 屬性 (如果有的話) 中顯示的文字指標。

*dwStyle*<br/>
視窗樣式。 如需完整清單，請參閱[CWnd：： CreateControl](reference/cwnd-class.md#createcontrol)。

*各種*<br/>
指定控制項的大小和位置。

*pParentWnd*<br/>
指定控制項的父視窗，通常是 `CDialog`。 不得為**Null**。

*nID*<br/>
指定控制項 ID，而且可以由容器使用以參考控制項。

使用此函式動態建立 ActiveX 控制項的範例會在 SDI 應用程式的表單檢視中。 您接著可以在應用程式的 `WM_CREATE` 處理常式中建立控制項的執行個體。

對於這個範例中，`CMyView` 是主要檢視類別，而 `CCirc` 是包裝函式類別，CIRC.H 則是包裝函式類別的標頭 (.H) 檔案。

實作此功能需要四個步驟。

### <a name="to-dynamically-create-an-activex-control-in-a-non-dialog-window"></a>若要在非對話方塊視窗中動態建立 ActiveX 控制項

1. 只要在 `CMyView` 類別定義之前，於 CMYVIEW.H 中插入 CIRC.H：

   [!code-cpp[NVC_MFC_AxCont#12](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]

1. 將成員變數 (為 `CCirc` 類型) 新增至位於 CMYVIEW.H 的 `CMyView` 類別定義的受保護區段：

   [!code-cpp[NVC_MFC_AxCont#13](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]
    [!code-cpp[NVC_MFC_AxCont#14](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]

1. 將 `WM_CREATE` 訊息處理常式新增至類別 `CMyView`。

1. 在處理函式中， `CMyView::OnCreate` `Create` 使用**this**指標做為父視窗，呼叫控制項的函式：

   [!code-cpp[NVC_MFC_AxCont#15](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]

1. 請重建專案。 每當應用程式檢視建立時，Circ 控制項就會動態建立。

## <a name="see-also"></a>另請參閱

[ActiveX 控制項容器](activex-control-containers.md)
