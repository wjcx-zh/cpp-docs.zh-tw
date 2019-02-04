---
title: 轉換點陣圖為工具列 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.newtoolbarresource
helpviewer_keywords:
- bitmaps [C++], converting to toolbars
- Toolbar editor [C++], converting bitmaps
- toolbars [C++], converting bitmaps
- New Toolbar Resource dialog box [C++]
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
ms.openlocfilehash: 31b684ff72e970a6b09748b3925564b0b372d339
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702696"
---
# <a name="converting-bitmaps-to-toolbars-c"></a>轉換點陣圖為工具列 （c + +）

轉換點陣圖，您可以在 c + + 專案中建立新的工具列。 從點陣圖圖形將轉換成工具列按鈕影像。 通常，點陣圖包含數個按鈕上的映像單一的點陣圖，使用一個映像的每個按鈕。 映像可以是任何大小;預設值是 16 像素寬和影像的高度。 您可以指定在按鈕影像的大小**新增工具列資源**當您選擇的對話方塊**工具列編輯器**從**映像**影像編輯器中的功能表。

**新增工具列資源**對話方塊可讓您指定您要新增工具列資源在 c + + 專案中的按鈕的高度與寬度。 預設值是 16 × 15 像素。

用來建立工具列點陣圖具有最大寬度為 2048年。 因此，如果您設定** 按鈕寬度**設為 512，您只能有四個按鈕。 如果您將寬度設成 513，您只能有三個按鈕。

對話方塊具有下列屬性：

|屬性|描述|
|---|---|
|**按鈕寬度**|提供空間讓您輸入要從一個點陣圖資源轉換成工具列資源的工具列按鈕的寬度。 映像會裁剪成指定的高度與寬度和色彩會調整為使用標準工具列色彩 （16 種色彩）。|
|**按鈕高度**|提供空間讓您輸入要從一個點陣圖資源轉換成工具列資源的工具列按鈕的高度。 映像會裁剪成指定的高度與寬度和色彩會調整為使用標準工具列色彩 （16 種色彩）。|

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="to-convert-bitmaps-to-a-toolbar"></a>若要將點陣圖轉換成工具列

1. 開啟現有的點陣圖資源中[影像編輯器](../windows/image-editor-for-icons.md)。 (如果點陣圖沒有.rc 檔，以滑鼠右鍵按一下.rc 檔，請選擇**匯入**從捷徑功能表中，瀏覽至您想要新增至您的.rc 檔，點陣圖，然後選取**開啟**。)

1. 從**映像**功能表上，選擇**工具列編輯器**。

   **新增工具列資源** 對話方塊隨即出現。 您可以變更圖示影像，以符合點陣圖的高度與寬度。 工具列影像即會顯示在工具列編輯器中。

1. 若要完成轉換，將變更命令**識別碼** 按鈕使用[屬性 視窗](/visualstudio/ide/reference/properties-window)。 輸入新**識別碼**或選取**識別碼**從下拉式清單。

   > [!TIP]
   > **屬性**視窗包含標題列中的圖釘按鈕。 選取此按鈕啟用或停用**自動隱藏**視窗。 若要快速循環顯示所有工具列按鈕屬性而不必重新開啟個別的屬性視窗，開啟**自動隱藏**關閉所以**屬性** 視窗會保持不動。

您也可以藉由變更命令 Id，新的工具列上的按鈕[屬性 視窗](/visualstudio/ide/reference/properties-window)。 編輯新的工具列上的資訊，請參閱[建立、 移動和編輯工具列按鈕](../windows/creating-moving-and-editing-toolbar-buttons.md)。

## <a name="requirements"></a>需求

MFC 或 ATL

## <a name="see-also"></a>另請參閱

[建立新的工具列](../windows/creating-new-toolbars.md)<br/>
[工具列編輯器](../windows/toolbar-editor.md)<br/>
[工具列按鈕屬性](../windows/toolbar-button-properties.md)<br/>
