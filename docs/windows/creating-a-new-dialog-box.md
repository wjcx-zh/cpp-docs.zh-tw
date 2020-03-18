---
title: 如何：建立對話方塊（C++）
ms.date: 02/15/2019
helpviewer_keywords:
- dialog boxes [C++], creating
- Dialog Editor [C++], creating dialog boxes
- modal dialog boxes [C++], logon screens
- logon screens
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
ms.openlocfilehash: 380cf58180913f538c1c326d6aaf49947b694063
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445412"
---
# <a name="how-to-create-a-dialog-box-c"></a>如何：建立對話方塊（C++）

C++對話方塊的位置和大小，以及其中控制項的位置和大小，都是以對話方塊單位來測量。 個別控制項的值和對話方塊會在您選取時，出現在 Visual Studio 狀態列的右下方。

> [!NOTE]
> 如果您的專案尚未包含 .rc 檔，請參閱[建立新的資源腳本](../windows/how-to-create-a-resource-script-file.md)檔。

## <a name="how-to"></a>作法

**對話方塊編輯器**可讓您：

### <a name="to-create-a-new-dialog-box"></a>若要建立新的對話方塊

1. 在[資源檢視](how-to-create-a-resource-script-file.md#create-resources)中，以滑鼠右鍵按一下 *.rc*檔，然後選取 [**新增資源**]。

1. 在 [**新增資源**] 對話方塊中，選取 [**資源類型**] 清單中的 [**對話方塊]** ，然後選擇 [**新增**]。

   如果**對話方塊**資源類型旁出現一個加號（ **+** ），表示該對話方塊範本可供使用。 選取加號展開範本清單，選取範本，然後選擇 [**新增**]。

   [新增] 對話方塊隨即在**對話方塊編輯器**中開啟。

您也可以在對話方塊編輯器中開啟現有的對話方塊以進行編輯。

### <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>若要建立使用者無法結束的對話方塊

您可以建立一個使用者無法結束的執行時間對話方塊。 這種對話方塊對登入以及鎖定應用程式或文件非常實用。

1. 在對話方塊的 [屬性] 窗格中，將 [系統功能表] 屬性設為 [false]。

   此設定會停用對話方塊系統功能表和 [**關閉**] 按鈕。

1. 在對話方塊表單中，刪除 [取消] 和 [確定] 按鈕。

   在執行時間，使用者無法結束具有這些特性的強制回應對話方塊。

若要啟用這種對話方塊的測試，[測試] 對話方塊功能會在按下**Esc 鍵**時偵測到。 **Esc**也稱為 VK_ESCAPE 虛擬索引鍵。 無論對話方塊在執行時間的設計方式為何，您都可以按下**Esc 鍵**來結束測試模式。

> [!NOTE]
> 對於 MFC 應用程式，若要建立使用者無法結束的對話方塊，您必須覆寫 `OnOK` 和 `OnCancel` 的預設行為，因為即使刪除相關聯的按鈕，仍然可以按**enter**或**Esc 鍵**來關閉對話方塊。

### <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>若要指定對話方塊的位置和大小

您可以在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)中設定屬性，以指定對話方塊出現在螢幕上的位置。

- 布林值**中心**屬性。

   如果您將此值設定為**True**，對話方塊將一律會出現在畫面的中央。 如果您將此屬性設定為**False**，則可以設定**XPos**和**YPos**屬性。

- **XPos**和**YPos**屬性，用來明確定義對話方塊出現在螢幕上的位置。

   這些位置屬性是視圖區域左上角的位移值，其定義為 `{X=0, Y=0}`。

- 會影響位置的**絕對對齊**屬性。

   如果**為 True**，則座標會相對於螢幕。 如果**為 False**，則表示座標是相對於對話方塊擁有者的視窗。

### <a name="to-test-a-dialog-box"></a>測試對話方塊

當您設計對話方塊時，您可以模擬和測試其執行階段行為，而不用重新編譯程式。 在這個模式下，您可以：

- 輸入文字、從下拉式方塊清單中選取、開啟或關閉選項，以及選擇命令。

- 測試定位順序。

- 測試控制項群組，例如選項按鈕和核取方塊。

- 為對話方塊中的控制項，測試鍵盤快速鍵。

> [!NOTE]
> 模擬中不包含使用嚮導所建立之對話方塊程式碼的連接。

當您測試對話方塊時，它通常會在相對於主程式視窗的位置顯示。 如果您已將對話方塊的 [**絕對對齊**] 屬性設定為 [ **True**]，則對話方塊會顯示在相對於螢幕左上角的位置。

1. 當**對話方塊編輯器**是使用中視窗時，請移至 [功能表**格式**] > [**測試] 對話方塊**。

1. 若要結束模擬，請按**Esc**鍵，或在您要測試的對話方塊中選取 [**關閉**] 按鈕。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊編輯器](../windows/dialog-editor.md)<br/>
[如何：管理對話方塊控制項](../windows/controls-in-dialog-boxes.md)<br/>