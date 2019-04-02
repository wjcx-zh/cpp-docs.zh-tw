---
title: HOW TO：新增功能區控制項和事件處理常式
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
ms.openlocfilehash: c21e8b86962ebf37ca1a06bae056d09b9a9dbb2f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58770119"
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>HOW TO：新增功能區控制項和事件處理常式

功能區控制項是項目，例如按鈕和下拉式方塊中，您加入至面板。 面板會顯示相關的控制項群組的功能區列區域。

本主題中，您開啟功能區設計工具、 新增按鈕，以及將連結顯示"Hello World"的事件。

### <a name="to-open-the-ribbon-designer"></a>若要開啟 功能區設計工具

1. 在 Visual Studio 中，在**檢視**功能表上，按一下**資源檢視**。

1. 在 **資源檢視**，連按兩下 功能區資源，以顯示設計介面上。

### <a name="to-add-a-button-and-an-event-handler"></a>若要加入按鈕和事件處理常式

1. 從 **工具列**，按一下 **按鈕** 並將它拖曳至設計介面中的面板。

1. 以滑鼠右鍵按一下  按鈕，然後按一下 **加入事件處理常式**。

1. 在 **事件處理常式精靈**，確認預設設定，然後按一下**加入和編輯**。 如需詳細資訊，請參閱 <<c0> [ 事件處理常式精靈](../ide/event-handler-wizard.md)。

1. 在程式碼編輯器中，將下列程式碼新增至處理常式函式：

```
    MessageBox((LPCTSTR)L"Hello World");
```

## <a name="see-also"></a>另請參閱

[RibbonGadgets 範例：功能區小工具應用程式](../overview/visual-cpp-samples.md)<br/>
[功能區設計工具 (MFC)](../mfc/ribbon-designer-mfc.md)
