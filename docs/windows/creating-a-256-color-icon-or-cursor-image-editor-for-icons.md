---
title: 使用 256 色調色盤 (圖示影像編輯器)
ms.date: 11/04/2016
helpviewer_keywords:
- 256-color palette
- cursors [C++], color
- colors [C++], icons
- colors [C++], cursors
- icons, color
- colors [C++], icons and cursors
- color palettes, 256-color
- palettes, 256-color
ms.assetid: 2738089b-4fd3-4c45-96ae-6a15e4c6b780
ms.openlocfilehash: 4e2f2c9ce58799756137bb47db42e52c97a43d39
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702891"
---
# <a name="using-the-256-color-palette-image-editor-for-icons"></a>使用 256 色調色盤 (圖示影像編輯器)

使用**映像**編輯器、 圖示和游標，則可以是大小大 (64 × 64) 與 256 色調色盤可從中選擇。 建立資源之後，請選取裝置影像樣式。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="to-create-a-256-color-icon-or-cursor"></a>若要建立 256 色圖示或游標

1. 在 [資源檢視](../windows/resource-view-window.md)，以滑鼠右鍵按一下.rc 檔，然後選擇**插入資源**從捷徑功能表。 (如果您已經有現有的映像資源在.rc 檔案中，例如資料指標中，您可以以滑鼠右鍵按一下**游標**資料夾，然後選取**插入游標**從捷徑功能表。)

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 在 [插入資源對話方塊](../windows/add-resource-dialog-box.md)，選取**圖示**或**游標**，然後選擇 **新增**。

1. 在 **映像**功能表上，選取**新的裝置影像**。

1. 選取您想要的 256 色影像樣式。

## <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>若要從大圖示的 256 色調色盤選擇色彩

若要繪製選取 256 色調色盤中，您必須選取色彩**色彩**中的調色盤[色彩視窗](../windows/colors-window-image-editor-for-icons.md)。

1. 選取 大圖示或游標，或建立新的大圖示或游標。

1. 從顯示中的 256 色彩選擇色彩**色彩**中的調色盤**色彩**視窗。

   選取的色彩會變成目前的色彩**色彩**中的調色盤**色彩**視窗。

   > [!NOTE]
   > 256 色的映像所使用的初始調色盤比對所傳回的調色盤`CreateHalftonePalette`Windows API。 適用於 Windows shell 的所有圖示應該都使用這個調色盤來防止重繪閃動期間調色盤實現。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[圖示和游標：顯示裝置的影像資源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)
