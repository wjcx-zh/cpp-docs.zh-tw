---
title: 建立裝置影像 (圖示影像編輯器)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.icon
- vc.editors.newimagetype
- vc.editors.customimage
- vc.editors.opendeviceimage
helpviewer_keywords:
- cursors [C++], creating
- icons [C++], creating
- display devices [C++], creating image
- images [C++], creating for display devices
- icons [C++], inserting
- New <Device> Image Type dialog box [C++]
- Custom Image dialog box [C++]
- Open <Device> Image dialog box [C++]
ms.assetid: 5a536928-32df-4ace-beb1-1521ce3b871f
ms.openlocfilehash: ce1069f6f410d7a60d631461086ca8870ef679c0
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560292"
---
# <a name="creating-a-device-image-image-editor-for-icons"></a>建立裝置影像 (圖示影像編輯器)

當您建立新的圖示或游標資源**映像**先在特定的樣式 （32 × 32，16 種色彩圖示和 32 × 32，資料指標的單色） 中建立映像的編輯器。 然後將映像不同大小和樣式加入初始的圖示或游標，並視需要編輯每個額外的映像，適用於不同的顯示裝置。 您也可以使用剪下和貼上作業，從現有的映像類型，或從圖形程式中建立點陣圖，以編輯映像。

當您開啟中的圖示或游標資源[影像編輯器](../windows/image-editor-for-icons.md)，預設會開啟大部分十分符合目前的顯示裝置的映像。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="new-ltdevicegt-image-type-dialog-box"></a>新&lt;裝置&gt;影像類型對話方塊

**的新&lt;裝置&gt;映像類型**對話方塊可讓您建立指定類型的新裝置映像。 若要開啟 **新增\<裝置 > 影像**對話方塊中，選取**新的映像類型**上**映像**功能表。 下列的屬性，包括**目標映像類型**並**自訂**。

### <a name="target-image-type"></a>目標影像類型

列出可用的映像類型。 選取您想要開啟的映像類型：

||||
|-|-|-|
|-16 x 16，16 種色彩|-48 x 48，16 種色彩|-96 x 96，16 種色彩|
|-16 x 16，256 色|-48 x 48，256 色|-96 x 96，256 色|
|-16 x 16，單色|-48 x 48，單色|-96 x 96，單色|
|-32 x 32，16 種色彩|-64 x 64，16 種色彩||
|-32 x 32，256 色|-64 x 64，256 色||
|-32 x 32，單色|-64 x 64，單色||

> [!NOTE]
> 這份清單中，將不會顯示任何現有的映像。

### <a name="custom"></a>自訂

會開啟**自訂映像**對話方塊中，您可以在其中建立新的映像使用自訂的大小和色彩數目。

**自訂映像**對話方塊可讓您建立新的映像的自訂大小和色彩數目。 會包含下列屬性：

|屬性|描述|
|---|---|
|[寬度]|提供空間讓您輸入自訂影像的寬度，單位為像素 （1-512，限制為 2048年）。|
|[高度]|提供空間讓您輸入高度的像素為單位 （1-512，限制為 2048年） 的自訂映像。|
|**色彩**|提供空間讓您選擇的自訂映像的色彩數目：2、 16 或 256。|

## <a name="open-ltdevicegt-image-dialog-box"></a>開啟&lt;裝置&gt;影像對話方塊

使用**開啟&lt;裝置&gt;映像**對話方塊中，以開啟 c + + 專案中的 裝置映像。 它會列出目前的資源 （屬於目前的資源的映像） 的現有裝置映像。 是包含下列屬性：

|屬性|描述|
|---|---|
|**目前的映像**|列出資源中包含的映像。 選取您想要開啟的影像類型。|

## <a name="to-create-a-new-icon-or-cursor"></a>若要建立新的圖示或游標

1. 在 [資源檢視](../windows/resource-view-window.md)，以滑鼠右鍵按一下.rc 檔，然後選擇**插入資源**從捷徑功能表。 (如果您已經有現有的映像資源在.rc 檔案中，例如資料指標中，您可以以滑鼠右鍵按一下**游標**資料夾，然後選取**插入游標**從捷徑功能表。)

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 在 [插入資源對話方塊](../windows/add-resource-dialog-box.md)，選取**圖示**或**游標**，然後選擇 **新增**。 圖示，此動作會建立具有 32 × 32、 16 色圖示的圖示資源。 資料指標，32 × 32，會建立單色 （2-色彩） 映像。

   如果一個加號 (**+**) 中的映像資源類型旁邊會出現**插入資源** 對話方塊中，表示工具列範本可供使用。 選取加號，展開 範本清單中的，選取範本，然後選擇**新增**。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[圖示和游標：顯示裝置的影像資源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[圖示和游標：顯示裝置的影像資源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[影像功能表](../windows/image-menu-image-editor-for-icons.md)<br/>
[圖示影像編輯器](../windows/image-editor-for-icons.md)<br/>
