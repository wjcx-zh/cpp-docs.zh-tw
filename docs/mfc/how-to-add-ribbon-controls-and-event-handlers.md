---
title: 如何：加入功能區控制項和事件處理常式
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
ms.openlocfilehash: d6382c8ebf73fe7a26b3950cc1965b229c22dbb7
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501225"
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>如何：加入功能區控制項和事件處理常式

功能區控制項是您加入至面板的元素，例如按鈕和下拉式方塊。 面板是功能區列的區域，可顯示一組相關的控制項。

在本主題中，您將開啟 [功能區設計工具]、[加入] 按鈕，然後連結顯示 "Hello World" 的事件。

### <a name="to-open-the-ribbon-designer"></a>開啟功能區設計工具

1. 在 Visual Studio 的 [ **View** ] 功能表上，按一下 [ **資源檢視**]。

1. 在 **資源檢視**中，按兩下功能區資源，以在設計介面上顯示它。

### <a name="to-add-a-button-and-an-event-handler"></a>若要加入按鈕和事件處理常式

1. 從 **工具列**中，按一下 [ **按鈕** ]，然後將它拖曳至設計介面中的面板。

1. 以滑鼠右鍵按一下按鈕，然後按一下 [ **新增事件處理常式**]。

1. 在 [ **事件處理常式]** 中，確認預設設定，然後按一下 [ **新增] 和 [編輯**]。 如需詳細資訊，請參閱 [事件處理常式 Wizard](../ide/adding-an-event-handler-visual-cpp.md#event-handler-wizard)。

1. 在 [程式碼編輯器] 中，將下列程式碼加入至處理常式函式：

```
    MessageBox((LPCTSTR)L"Hello World");
```

## <a name="see-also"></a>另請參閱

[RibbonGadgets 範例：功能區小工具應用程式](../overview/visual-cpp-samples.md)<br/>
[ (MFC 的功能區設計工具) ](ribbon-designer-mfc.md)
