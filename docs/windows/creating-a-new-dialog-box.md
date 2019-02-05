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
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
ms.openlocfilehash: 928432000fb9a6347433b78b224e15f07ce810d2
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742644"
---
# <a name="creating-a-dialog-box-c"></a>建立對話方塊 （c + +）

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

如需有關如何將資源加入 managed 專案的資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[如何：建立資源](../windows/how-to-create-a-resource.md)<br/>
[資源檔](../windows/resource-files-visual-studio.md)<br/>
[對話方塊編輯器](../windows/dialog-editor.md)