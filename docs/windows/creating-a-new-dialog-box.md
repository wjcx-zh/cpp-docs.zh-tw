---
title: 如何：建立對話方塊 （c + +）
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog
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
ms.openlocfilehash: 51ff52aefb5586b4e301831dbdebeb783ec3c4c5
ms.sourcegitcommit: b4645761ce5acf8c2fc7a662334dd5a471ea976d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/07/2019
ms.locfileid: "57563198"
---
# <a name="how-to-create-a-dialog-box-c"></a>HOW TO：建立對話方塊 （c + +）

與位置的大小 [c + +] 對話方塊中，以及位置和大小的控制項，會以對話方塊單位。 個別控制項和對話方塊中的值會出現在右下角的 Visual Studio 狀態列上選取它們。

> [!NOTE]
> 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

## <a name="how-to"></a>如何

**對話方塊編輯器**可讓您：

### <a name="to-create-a-new-dialog-box"></a>若要建立新的對話方塊

1. 在 [資源檢視](/windows/how-to-create-a-resource-script-file#create-resources)，以滑鼠右鍵按一下您 *.rc*檔案，然後選取**加入資源**。

1. 在 **加入資源**對話方塊中，選取**對話方塊**中**資源類型**清單，然後選擇**新增**。

   如果一個加號 (**+**) 旁邊會出現**對話方塊**資源類型，表示對話方塊範本都可用。 選取加號，展開 範本清單中的，選取範本，然後選擇**新增**。

   在中，開啟 [新增] 對話方塊**對話方塊編輯器**。

您也可以在對話方塊編輯器中開啟現有的對話方塊，進行編輯。

### <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>若要建立使用者無法結束的對話方塊

您可以建立使用者無法結束的執行階段對話方塊。 這種對話方塊對登入以及鎖定應用程式或文件非常實用。

1. 在對話方塊的 [屬性]  窗格中，將 [系統功能表]  屬性設為 [false] 。

   此設定會停用對話方塊系統功能表並**關閉** 按鈕。

1. 在對話方塊表單中，刪除 [取消]  和 [確定]  按鈕。

   在執行階段，使用者無法結束具有下列特性的強制回應對話方塊。

若要啟用這種對話方塊中的測試，測試對話方塊函式偵測到的時機**Esc**按下。 **Esc**亦稱為 VK_ESCAPE 虛擬按鍵。 不論如何對話方塊中，設計來在執行階段行為，您可以結束測試模式藉由按下**Esc**。

> [!NOTE]
> 針對 MFC 應用程式，若要建立對話方塊，使用者無法結束，您必須覆寫預設行為`OnOK`並`OnCancel`因為即使刪除相關聯的按鈕時，對話方塊仍關閉按**請輸入**或是**Esc**。

### <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>若要指定的位置和大小的對話方塊

您可以在設定的屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)指定對話方塊會出現在螢幕上。

- 布林值**Center**屬性。

   如果您將值設定為 **，則為 True**，對話方塊一律會出現在螢幕的中央。 如果您將這個屬性設定為**假**，然後您可以設定**XPos**並**YPos**屬性。

- **XPos**並**YPos**用來明確定義在螢幕上的屬性對話方塊隨即出現。

   這些位置屬性會從左上角的 [檢視] 區域中，因為其定義如下的位移的值`{X=0, Y=0}`。

- **Absolute Align**影響位置的屬性。

   如果 **，則為 True**，座標是相對於畫面。 如果**False**，座標是相對於對話方塊擁有者的視窗。

### <a name="to-test-a-dialog-box"></a>測試對話方塊

當您設計對話方塊時，您可以模擬和測試其執行階段行為，而不用重新編譯程式。 在這個模式下，您可以：

- 輸入文字、從下拉式方塊清單中選取、開啟或關閉選項，以及選擇命令。

- 測試定位順序。

- 測試控制項群組，例如選項按鈕和核取方塊。

- 為對話方塊中的控制項，測試鍵盤快速鍵。

> [!NOTE]
> 連接對話方塊程式碼使用精靈不包含在此模擬。

當您測試對話方塊時，它通常會在相對於主程式視窗的位置顯示。 如果您已經設定的對話方塊**Absolute Align**屬性設 **，則為 True**，對話方塊會顯示在相對於螢幕左上角的位置。

1. 當**對話方塊編輯器**是作用中視窗中，移至功能表**格式** > **測試對話方塊**。

1. 若要結束模擬，請按**Esc**或選取**關閉**在對話方塊中，您要測試的按鈕。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊編輯器](../windows/dialog-editor.md)<br/>
[如何：管理對話方塊控制項](../windows/controls-in-dialog-boxes.md)<br/>