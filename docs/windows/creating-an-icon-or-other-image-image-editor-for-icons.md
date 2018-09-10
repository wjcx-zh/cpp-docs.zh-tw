---
title: 建立圖示或其他影像 （圖示影像編輯器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
dev_langs:
- C++
helpviewer_keywords:
- bitmaps [C++]
- images [C++], creating
- resources [C++], creating images
- bitmaps [C++], creating
- graphics [C++], creating
- Image editor [C++], creating images
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 82479dab780fce677eeee84c4ccde880fe19d2bc
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314907"
---
# <a name="creating-an-icon-or-other-image-image-editor-for-icons"></a>建立圖示或其他影像 (圖示影像編輯器)

您可以建立新的影像 （點陣圖、 圖示、 游標或工具列），然後使用影像編輯器來自訂其外觀。 您也可以建立新的點陣圖，模仿[範本](../windows/how-to-use-resource-templates.md)。

### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>若要將新的映像資源新增至未受管理的 c + + 專案

1. 在 [資源檢視](../windows/resource-view-window.md)，以滑鼠右鍵按一下.rc 檔，然後選擇**插入資源**從捷徑功能表。 (如果您已經有現有的映像資源在.rc 檔案中，例如資料指標中，您可以直接以滑鼠右鍵按一下**游標**資料夾，然後選取**插入游標**從捷徑功能表。)

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 在 [插入資源對話方塊](../windows/add-resource-dialog-box.md)，選取您想要建立的映像資源的類型 (**點陣圖**，例如) 然後按一下**新增**。

   如果一個加號 (**+**) 中的映像資源類型旁邊會出現**插入資源** 對話方塊中，表示工具列範本可供使用。 按一下加號，展開 範本清單，選取範本，然後按一下**新增**。

### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>若要將新的映像資源新增至.NET 程式設計語言中的專案

1. 在 [**方案總管] 中**，以滑鼠右鍵按一下專案資料夾 (例如`WindowsApplication1`)。

2. 從快顯功能表中，按一下**新增**，然後選擇**加入新項目**。

3. 在 **類別** 窗格中，展開**本機專案項目**資料夾，然後選擇 **資源**。

4. 在 [**範本**] 窗格中，選擇您想要新增至專案的資源類型。

   資源便會加入至您的專案中**方案總管**並在中開啟資源[影像編輯器](../windows/image-editor-for-icons.md)。 您現在可以使用影像編輯器中可用的所有工具，修改您的映像。 如需有關如何將影像加入至 managed 專案的詳細資訊，請參閱[在設計階段載入圖片](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms)。

   > [!NOTE]
   > 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。 如需詳細資訊，請參閱 <<c0> [ 建立資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)中 *.NET Framework 開發人員指南*。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[圖示和游標： 顯示裝置的影像資源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)  
[轉換點陣圖為工具列](../windows/converting-bitmaps-to-toolbars.md)  
[建立新的工具列](../windows/creating-new-toolbars.md)  
[編輯圖形資源](../windows/editing-graphical-resources-image-editor-for-icons.md)  
[圖示影像編輯器](../windows/image-editor-for-icons.md)