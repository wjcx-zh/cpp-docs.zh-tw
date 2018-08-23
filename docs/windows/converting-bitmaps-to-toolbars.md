---
title: 轉換點陣圖為工具列 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bitmaps [C++], converting to toolbars
- Toolbar editor, converting bitmaps
- toolbars [C++], converting bitmaps
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d5524b1d5ecb3fa4de38f46706f26d2a318fe5ef
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602396"
---
# <a name="converting-bitmaps-to-toolbars"></a>轉換點陣圖為工具列

您可以藉由轉換點陣圖建立新的工具列。 從點陣圖圖形將轉換成工具列按鈕影像。 通常，點陣圖包含數個按鈕上的映像單一的點陣圖，使用一個映像的每個按鈕。 映像可以是任何大小;預設值是 16 像素寬和影像的高度。 您可以指定在按鈕影像的大小[新增工具列資源對話方塊](../windows/new-toolbar-resource-dialog-box.md)當您選擇**工具列編輯器**從**映像**影像編輯器中的功能表。

### <a name="to-convert-bitmaps-to-a-toolbar"></a>若要將點陣圖轉換成工具列

1. 開啟現有的點陣圖資源中[影像編輯器](../windows/image-editor-for-icons.md)。 (如果點陣圖已不在您的.rc 檔，以滑鼠右鍵按一下.rc 檔，請選擇**匯入**從捷徑功能表中，瀏覽至您想要新增至您的.rc 檔，點陣圖，然後按一下**開啟**。)

2. 從**映像**功能表上，選擇**工具列編輯器**。

   [新增工具列資源對話方塊](../windows/new-toolbar-resource-dialog-box.md)隨即出現。 您可以變更圖示影像，以符合點陣圖的高度與寬度。 工具列影像即會顯示在工具列編輯器中。

3. 若要完成轉換，將變更命令**識別碼** 按鈕使用[屬性 視窗](/visualstudio/ide/reference/properties-window)。 輸入新**識別碼**或選取**識別碼**從下拉式清單。

   > [!TIP]
   > **屬性**視窗包含標題列中的圖釘按鈕。 按一下此按鈕啟用或停用**自動隱藏**視窗。 若要快速循環顯示所有工具列按鈕屬性而不必重新開啟個別的屬性視窗，開啟**自動隱藏**關閉所以**屬性** 視窗會保持不動。

您也可以藉由變更命令 Id，新的工具列上的按鈕[屬性 視窗](/visualstudio/ide/reference/properties-window)。 編輯新的工具列上的資訊，請參閱[建立、 移動和編輯工具列按鈕](../windows/creating-moving-and-editing-toolbar-buttons.md)。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

MFC 或 ATL

## <a name="see-also"></a>另請參閱

[建立新的工具列](../windows/creating-new-toolbars.md)  
[工具列編輯器](../windows/toolbar-editor.md)