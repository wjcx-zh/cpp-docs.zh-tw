---
title: 如何：加入功能區控制項和事件處理常式
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
ms.openlocfilehash: 560524c36dbf57faec3b4b6372cade047f9fe7de
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618476"
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>如何：加入功能區控制項和事件處理常式

功能區控制項是您新增至面板的元素，例如按鈕和下拉式方塊。 面板是功能區列的區域，可顯示一組相關的控制項。

在本主題中，您將開啟功能區設計工具、加入按鈕，然後連結顯示「Hello World」的事件。

### <a name="to-open-the-ribbon-designer"></a>若要開啟功能區設計工具

1. 在 Visual Studio 的 [ **View** ] 功能表上，按一下 [**資源檢視**]。

1. 在**資源檢視**中，按兩下功能區資源，將它顯示在設計介面上。

### <a name="to-add-a-button-and-an-event-handler"></a>若要加入按鈕和事件處理常式

1. 從**工具列**按一下 [**按鈕**]，並將它拖曳至設計介面中的面板。

1. 以滑鼠右鍵按一下按鈕，然後按一下 [**新增事件處理常式**]。

1. 在 [**事件處理常式]** 中，確認預設設定，然後按一下 [**新增和編輯**]。 如需詳細資訊，請參閱[事件處理常式 Wizard](../ide/event-handler-wizard.md)。

1. 在 [程式碼編輯器] 中，將下列程式碼加入至處理函式：

```
    MessageBox((LPCTSTR)L"Hello World");
```

## <a name="see-also"></a>另請參閱

[RibbonGadgets 範例：功能區小工具應用程式](../overview/visual-cpp-samples.md)<br/>
[功能區設計工具 (MFC)](ribbon-designer-mfc.md)
