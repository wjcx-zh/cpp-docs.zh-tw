---
title: 建立對話方塊 （c + +）
ms.date: 11/04/2016
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
ms.openlocfilehash: a3b8143d3a70906f910a445816a188913a593e5d
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264812"
---
# <a name="creating-a-dialog-box-c"></a>建立對話方塊 （c + +）

與位置的大小 [c + +] 對話方塊中，以及位置和大小的控制項，會以對話方塊單位。 個別控制項和對話方塊中的值會出現在右下角的 Visual Studio 狀態列上選取它們。

當您設計對話方塊中時，您也可以模擬，並測試其執行階段行為，而不需要編譯您的程式。 在這個模式下，您可以：

- 輸入文字、從下拉式方塊清單中選取、開啟或關閉選項，以及選擇命令。

- 測試定位順序。

- 測試控制項群組，例如選項按鈕和核取方塊。

- 為對話方塊中的控制項，測試鍵盤快速鍵。

   > [!NOTE]
   > 使用精靈連接至對話方塊程式碼，不包含在此模擬中。

當您測試對話方塊時，它通常會在相對於主程式視窗的位置顯示。 如果您已經設定的對話方塊**Absolute Align**屬性設 **，則為 True**，對話方塊會顯示在相對於螢幕左上角的位置。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="to-create-a-new-dialog-box"></a>若要建立新的對話方塊

1. 在 [資源檢視](../windows/resource-view-window.md)，以滑鼠右鍵按一下.rc 檔，然後選擇**加入資源**從捷徑功能表。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 在 **加入資源**對話方塊中，選取**對話方塊**中**資源類型**清單，然後選擇**新增**。

   如果一個加號 (**+**) 旁邊會出現**對話方塊**資源類型，表示對話方塊範本都可用。 選取加號，展開 範本清單中的，選取範本，然後選擇**新增**。

   在中，開啟 [新增] 對話方塊 **對話方塊**編輯器。

   您也可以[ 對話方塊編輯器中開啟現有的對話方塊，編輯](../windows/viewing-and-editing-resources-in-a-resource-editor.md)。

## <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>若要建立使用者無法結束的對話方塊

您可以建立使用者無法結束的執行階段對話方塊。 這種對話方塊對登入以及鎖定應用程式或文件非常實用。

1. 在對話方塊的 [屬性]  窗格中，將 [系統功能表]  屬性設為 [false] 。

   此設定會停用對話方塊系統功能表並**關閉** 按鈕。

1. 在對話方塊表單中，刪除 [取消]  和 [確定]  按鈕。

   在執行階段，使用者無法結束具有下列特性的強制回應對話方塊。

若要啟用這種對話方塊中的測試，測試對話方塊函式偵測到的時機**Esc**按下。 (**Esc**亦稱為 VK_ESCAPE 虛擬按鍵。)不論如何對話方塊中，設計來在執行階段行為，您可以結束測試模式藉由按下**Esc**。

> [!NOTE]
> 針對 MFC 應用程式，若要建立對話方塊，使用者無法結束，您必須覆寫預設行為`OnOK`並`OnCancel`因為即使刪除相關聯的按鈕時，對話方塊仍關閉按**請輸入**或是**Esc**。

## <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>若要指定的位置和大小的對話方塊

有三個屬性，您可以在設定[屬性 視窗](/visualstudio/ide/reference/properties-window)指定對話方塊會出現在螢幕上。 **Center**屬性是布林值; 如果您將值設定為 **，則為 True**，對話方塊一律會出現在螢幕的中央。 如果您將它設定為**False**，然後您可以設定**XPos**並**YPos**屬性，以明確地定義在螢幕上會出現的對話方塊。 [位置] 屬性會從左上角的 [檢視] 區域中，因為其定義如下的位移的值`{X=0, Y=0}`。 位置也根據**Absolute Align**屬性： 如果 **，則為 True**，座標是相對於畫面; 如果**False**，座標是相對於對話方塊擁有者的視窗。

## <a name="to-test-a-dialog-box"></a>測試對話方塊

1. 當** 對話方塊**編輯器是使用中的視窗，在功能表列上，選擇**格式** > **測試對話方塊**。

1. 若要結束模擬，請按**Esc**，或只選擇**關閉**在對話方塊中，您要測試的按鈕。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[如何：建立資源](../windows/how-to-create-a-resource.md)<br/>
[資源檔](../windows/resource-files-visual-studio.md)<br/>
[對話方塊編輯器](../windows/dialog-editor.md)<br/>
[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)<br/>