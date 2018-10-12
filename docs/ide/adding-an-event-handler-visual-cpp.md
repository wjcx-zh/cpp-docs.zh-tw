---
title: 新增事件處理常式 (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.eventhandler.overview
dev_langs:
- C++
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd16628c48c30f6f554a842b70c5217753e305f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430302"
---
# <a name="adding-an-event-handler-visual-c"></a>加入事件處理常式 (Visual C++)

在資源編輯器中，您可以使用[事件處理常式精靈](../ide/event-handler-wizard.md)，為對話方塊方塊控制項新增事件處理常式，或編輯現有的事件處理常式。

您可以使用[屬性視窗](/visualstudio/ide/reference/properties-window)將事件新增至實作對話方塊的類別。 如果您想要將事件新增至對話方塊類別以外的類別，請使用 [事件處理常式精靈]。

### <a name="to-add-an-event-handler-to-a-dialog-box-control"></a>將事件處理常式新增至對話方塊控制項

1. 在[資源檢視](../windows/resource-view-window.md)中按兩下對話方塊資源，在[對話方塊編輯器](../windows/dialog-editor.md)中開啟包含控制項的對話方塊資源。

1. 以滑鼠右鍵按一下您想要處理通知事件的控制項。

1. 在捷徑功能表，按一下 [新增事件處理常式]，顯示 [事件處理常式精靈]。

1. 在 [訊息類型] 方塊中選取事件，將其新增至 [類別清單] 方塊中選取的類別。

1. 接受 [函式處理常式名稱] 方塊中的預設名稱，或提供您選擇的名稱。

1. 按一下 [新增並編輯]，將事件處理常式新增至專案，並在新函式處開啟文字編輯器來新增適當的事件處理常式程式碼。

   如果選取的訊息類型已經有所選取類別的事件處理常式，便無法使用 [新增並編輯]，而是可以使用 [編輯程式碼]。 按一下 [編輯程式碼]，開啟文字編輯器到達現有的函式處。

或者，您可以從 [屬性視窗](/visualstudio/ide/reference/properties-window)新增事件處理常式。 請參閱[新增對話方塊控制項的事件處理常式](../windows/adding-event-handlers-for-dialog-box-controls.md)以取得詳細資訊。

## <a name="see-also"></a>請參閱

[使用程式碼精靈新增功能](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[新增類別](../ide/adding-a-class-visual-cpp.md)<br>
[新增成員變數](../ide/adding-a-member-variable-visual-cpp.md)<br>
[新增成員函式](../ide/adding-a-member-function-visual-cpp.md)<br>
[MFC 訊息處理常式](../mfc/reference/adding-an-mfc-message-handler.md)<br>
[巡覽類別結構](../ide/navigating-the-class-structure-visual-cpp.md)