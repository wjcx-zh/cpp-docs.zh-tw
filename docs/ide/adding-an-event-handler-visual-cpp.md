---
title: 新增事件處理常式
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.eventhandler.overview
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
- event handler wizard [C++]
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
ms.openlocfilehash: 0d852991c29281a7ecf912bd3d764d9916ef10f7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447503"
---
# <a name="add-an-event-handler"></a>新增事件處理常式

在資源編輯器中，您可以使用[事件處理常式精靈](#event-handler-wizard)，為對話方塊方塊控制項新增事件處理常式，或編輯現有的事件處理常式。

您可以使用[屬性視窗](/visualstudio/ide/reference/properties-window)將事件新增至實作對話方塊的類別。 若要將事件新增至對話方塊類別以外的類別，請使用事件處理常式精靈。

**將事件處理常式新增至對話方塊控制項：**

1. 在[資源檢視](../windows/how-to-create-a-resource-script-file.md#create-resources)中按兩下對話方塊資源，在[對話方塊編輯器](../windows/dialog-editor.md)中開啟包含控制項的對話方塊資源。

1. 以滑鼠右鍵按一下您想要處理通知事件的控制項。

1. 在捷徑功能表上，選擇 [新增事件處理常式] 以顯示 [事件處理常式精靈]。

1. 在 [訊息類型] 方塊中選取事件，將其新增至 [類別清單] 方塊中選取的類別。

1. 接受 [函式處理常式名稱] 方塊中的預設名稱，或提供您選擇的名稱。

1. 選取 [新增並編輯]，將事件處理常式新增至專案，並在新函式處開啟文字編輯器來新增適當的事件處理常式程式碼。

   如果選取的訊息類型已經有所選取類別的事件處理常式，便無法使用 [新增並編輯]，而是可以使用 [編輯程式碼]。 選取 [編輯程式碼]，在現有的函式處開啟文字編輯器。

或者，您可以從 [屬性視窗](/visualstudio/ide/reference/properties-window)新增事件處理常式。 如需詳細資訊，請參閱[新增對話方塊控制項的事件處理常式](../windows/adding-event-handlers-for-dialog-box-controls.md)。

## <a name="in-this-section"></a>本節內容

- [事件處理常式精靈](#event-handler-wizard)

## <a name="event-handler-wizard"></a>事件處理常式精靈

此精靈會將對話方塊控制項的事件處理常式新增至您選擇的類別。 如果您從[屬性視窗](/visualstudio/ide/reference/properties-window)新增事件處理常式，則只能將它新增至實作對話方塊的類別。 如需詳細資訊，請參閱[新增對話方塊控制項的事件處理常式](../windows/adding-event-handlers-for-dialog-box-controls.md)。

- **命令名稱**

  指出為其新增事件處理常式的所選取控制項。 此方塊無法使用。

- **訊息類型**

  顯示所選取控制項目前可能的訊息處理常式的清單。

- **函式處理常式名稱**

  顯示新增來處理事件的函式名稱。 名稱預設為依據訊息類型和命令，並在前面加上 `On`。 例如，對於稱為 `IDC_BUTTON1` 的按鈕，訊息類型 `BN_CLICKED` 顯示函式處理常式名稱為 `OnBnClickedButton1`。

- **類別清單**

  顯示您可以新增事件處理常式的可用類別。 所選取對話方塊的類別會以紅色顯示。

- **處理常式描述**

  為 [訊息類型] 方塊中選取的項目提供描述。 此方塊無法使用。

- **新增和編輯**

  將訊息處理常式新增至選取的類別或物件。 它還會開啟文字編輯器到新函式，讓您能夠新增控制項通知的處理常式程式碼。

- **編輯程式碼**

  開啟文字編輯器到選取的現有函式，讓您能夠新增或編輯控制項通知處理常式的程式碼。
