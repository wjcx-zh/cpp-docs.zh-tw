---
title: 設計對話方塊 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
ms.openlocfilehash: 4a879f6bb1cdcd4b4897e510fb21d04500dfd3f2
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742683"
---
# <a name="designing-a-dialog-box-c"></a>設計對話方塊 （c + +）

與位置的大小 [c + +] 對話方塊中，以及位置和大小的控制項，會以對話方塊單位。 個別控制項和對話方塊中的值會出現在右下角的 Visual Studio 狀態列上選取它們。

當您設計對話方塊中時，您也可以模擬，並測試其執行階段行為，而不需要編譯您的程式。 在這個模式下，您可以：

- 輸入文字、從下拉式方塊清單中選取、開啟或關閉選項，以及選擇命令。

- 測試定位順序。

- 測試控制項群組，例如選項按鈕和核取方塊。

- 為對話方塊中的控制項，測試鍵盤快速鍵。

   > [!NOTE]
   > 使用精靈連接至對話方塊程式碼，不包含在此模擬中。

當您測試對話方塊時，它通常會在相對於主程式視窗的位置顯示。 如果您已經設定的對話方塊**Absolute Align**屬性設 **，則為 True**，對話方塊會顯示在相對於螢幕左上角的位置。

如需有關如何將資源加入 managed 專案的資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)。

## <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>若要指定的位置和大小的對話方塊

有三個屬性，您可以在設定[屬性 視窗](/visualstudio/ide/reference/properties-window)指定對話方塊會出現在螢幕上。 **Center**屬性是布林值; 如果您將值設定為 **，則為 True**，對話方塊一律會出現在螢幕的中央。 如果您將它設定為**False**，然後您可以設定**XPos**並**YPos**屬性，以明確地定義在螢幕上會出現的對話方塊。 [位置] 屬性會從左上角的 [檢視] 區域中，因為其定義如下的位移的值`{X=0, Y=0}`。 位置也根據**Absolute Align**屬性： 如果 **，則為 True**，座標是相對於畫面; 如果**False**，座標是相對於對話方塊擁有者的視窗。

## <a name="to-test-a-dialog-box"></a>測試對話方塊

1. 當** 對話方塊**編輯器是使用中的視窗，在功能表列上，選擇**格式** > **測試對話方塊**。

1. 若要結束模擬，請按**Esc**，或只選擇**關閉**在對話方塊中，您要測試的按鈕。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)<br/>
[對話方塊編輯器](../windows/dialog-editor.md)<br/>
[顯示或隱藏對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)