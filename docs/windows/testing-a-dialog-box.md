---
title: 測試對話方塊 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
ms.openlocfilehash: 101a2b556b2593953bfa6482f96d5b1aadc38d1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625055"
---
# <a name="testing-a-dialog-box-c"></a>測試對話方塊 （c + +）

當您設計對話方塊時，您可以模擬和測試其執行階段行為，而不用重新編譯程式。 在這個模式下，您可以：

- 輸入文字、從下拉式方塊清單中選取、開啟或關閉選項，以及選擇命令。

- 測試定位順序。

- 測試控制項群組，例如選項按鈕和核取方塊。

- 為對話方塊中的控制項，測試鍵盤快速鍵。

   > [!NOTE]
   > 使用精靈連接至對話方塊程式碼，不包含在此模擬中。

當您測試對話方塊時，它通常會在相對於主程式視窗的位置顯示。 如果您已經設定的對話方塊**Absolute Align**屬性設 **，則為 True**，對話方塊會顯示在相對於螢幕左上角的位置。

### <a name="to-test-a-dialog-box"></a>測試對話方塊

1. 當** 對話方塊**編輯器是使用中的視窗，在功能表列上，選擇**格式** > **測試對話方塊**。

2. 若要結束模擬，請按**Esc**，或只選擇**關閉**在對話方塊中，您要測試的按鈕。

如需有關如何將資源加入 managed 專案的資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)<br/>
[對話方塊編輯器](../windows/dialog-editor.md)<br/>
[顯示或隱藏對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)