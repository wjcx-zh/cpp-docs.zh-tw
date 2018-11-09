---
title: 事件處理常式精靈
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.eventhandler.overview
helpviewer_keywords:
- Event Handler Wizard [C++]
ms.assetid: af8e1835-94b1-4d9a-b353-c519e011d3a1
ms.openlocfilehash: e48d995aed0c59cc4ba7b645706448b5c3618b4a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654164"
---
# <a name="event-handler-wizard"></a>事件處理常式精靈

此精靈會將對話方塊控制項的事件處理常式新增至您選擇的類別。 如果您從[屬性視窗](/visualstudio/ide/reference/properties-window)新增事件處理常式，則只能將它新增至實作對話方塊的類別。 請參閱[新增對話方塊控制項的事件處理常式](../windows/adding-event-handlers-for-dialog-box-controls.md)以取得詳細資訊。

- **命令名稱**

   指出為其新增事件處理常式的所選取控制項。 此方塊無法使用。

- **訊息類型**

   顯示所選取控制項目前可能的訊息處理常式的清單。

- **函式處理常式名稱**

   顯示新增來處理事件的函式名稱。 根據預設，名稱是依據訊息類型和命令，並在前面加上 "On"。 例如，對於稱為 `IDC_BUTTON1` 的按鈕，訊息類型 `BN_CLICKED` 顯示函式處理常式名稱為 `OnBnClickedButton1`。

- **類別清單**

   顯示您可以新增事件處理常式的可用類別。 所選取對話方塊的類別會以紅色顯示。

- **處理常式描述**

   為 [訊息類型] 方塊中選取的項目提供描述。 此方塊無法使用。

- **新增和編輯**

   將訊息處理常式新增至選取的類別或物件，然後開啟文字編輯器到新函式，讓您能夠新增控制項通知處理常式的程式碼。

- **編輯程式碼**

   開啟文字編輯器到選取的現有函式，讓您能夠新增或編輯控制項通知處理常式的程式碼。

## <a name="see-also"></a>請參閱

[新增事件處理常式](../ide/adding-an-event-handler-visual-cpp.md)