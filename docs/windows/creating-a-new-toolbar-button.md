---
title: 建立新的工具列按鈕 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.toolbar
helpviewer_keywords:
- Toolbar editor [C++], creating buttons
- toolbar buttons [C++], button image
- toolbar buttons [C++], creating
- toolbar buttons (in Toolbar editor)
ms.assetid: 46c120fe-4f2a-4887-a08f-bd1fea04b3f4
ms.openlocfilehash: 1fe3e960ea9d2cec36e1c0d1ee9edb30bcc354d4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512498"
---
# <a name="creating-a-new-toolbar-button-c"></a>建立新的工具列按鈕 （c + +）

### <a name="to-create-a-new-toolbar-button"></a>若要建立新的工具列按鈕

1. 在 [資源檢視](../windows/resource-view-window.md)展開 [資源] 資料夾 (例如，Project1.rc)。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 依序展開**工具列**資料夾，然後選取要編輯的工具列。

3. 空白的按鈕，工具列的右端指派識別碼。 則可以藉由編輯**識別碼**中的屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)。 比方說，您可以為工具列按鈕提供相同的 ID 為功能表選項。 在此情況下，使用下拉式清單方塊來選取**識別碼**的功能表選項。

   -或-

   選取 [空白] 按鈕的工具列的右端 (在**工具列檢視**窗格)，並開始繪圖。 指派的預設按鈕的命令識別碼 (ID_BUTTON\<n >)。

您也可以複製並貼上到做為新按鈕的工具列上的映像。

### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>若要將影像加入為按鈕的工具列

1. 在 [資源檢視](../windows/resource-view-window.md)，按兩下 [開啟] 工具列。

2. 接下來，開啟您想要新增至您的工具列影像。

   > [!NOTE]
   > 如果您在 Visual Studio 中開啟映像，即會開啟在**映像**編輯器。 您也可以開啟在其他圖形程式中的映像。

3. 從**編輯**功能表上，選擇**複製**。

4. 在 [來源] 視窗頂端的索引標籤，即可切換至您的工具列。

5. 從**編輯**功能表上，選擇**貼上**。

   映像會出現在工具列中，為新的按鈕。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

MFC 或 ATL

## <a name="see-also"></a>另請參閱

[工具列按鈕屬性](../windows/toolbar-button-properties.md)<br/>
[建立、移動和編輯工具列按鈕](../windows/creating-moving-and-editing-toolbar-buttons.md)<br/>
[工具列編輯器](../windows/toolbar-editor.md)