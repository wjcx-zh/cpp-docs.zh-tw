---
title: 工具列 （c + + 圖示影像編輯器）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
- vc.editors.texttool
helpviewer_keywords:
- Graphics toolbar
- Image editor [C++], toolbar
- Image editor [C++], Option selector
- Properties window
- Option selector, Image editor
- toolbars [C++], showing
- toolbars [C++], hiding
- text, adding to an image
- Text Tool dialog box [C++]
- Text Tool Font dialog box [C++]
- fonts, changing on an image
- text, on images
ms.assetid: a0af4209-6273-4106-a7c1-0edecc9b5755
ms.openlocfilehash: dfbd721afd997f3151b1c20a7e0e1fb60e0c83e4
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560318"
---
# <a name="toolbar-c-image-editor-for-icons"></a>工具列 （c + + 圖示影像編輯器）

**影像編輯器**工具列包含工具，繪圖、 繪圖、 輸入文字、 消除及操作檢視。 它也包含選項選取器，與中，您可以選取使用各項工具的選項。 例如，您可以選擇不同的筆刷寬度、 縮放因素和線條樣式。

> [!NOTE]
> 上提供的所有工具**影像編輯器**工具列也會提供從**映像**功能表 (在**工具**命令)。

![影像編輯器工具列](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar")影像編輯器工具列

若要使用**影像編輯器**工具列並**選項**選取器中，選取 工具或您想要的選項。

> [!TIP]
> 將游標停留在工具列按鈕時，就會出現工具提示。 這些提示可協助您識別每個按鈕的功能。

具有**選項**選取器，您可以指定一條線、 筆刷筆劃和更多功能的寬度。 上的圖示**選項**選取器按鈕變更，視哪一種工具而定，您已選取。

![繪製&#45;影像編輯器工具列上的形狀選取器](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector")影像編輯器工具列上的選項選取器

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="use-the-text-tool-dialog-box"></a>使用文字工具對話方塊

使用**文字工具**對話方塊中，將文字加入至資料指標、 點陣圖或圖示的資源。

若要存取此對話方塊中，開啟[影像編輯器](../windows/window-panes-image-editor-for-icons.md)。 選取 **工具**從**映像**功能表，然後再選取**文字工具**命令。

### <a name="font-button"></a>[字型] 按鈕

會開啟**文字工具字型**對話方塊中，您可以在其中變更字型、 樣式或資料指標字型的大小。 變更會套用至中顯示的文字**文字**區域。

若要存取此對話方塊中，選取**字型**按鈕**文字工具** 對話方塊。 可用的屬性如下：

|屬性|描述|
|---|---|
|**字型**|列出可用的字型。|
|[字型樣式]|列出指定的字型的可用樣式。|
|**Size**|列出指定的字型的可用點數大小。|
|**範例**|顯示文字會如何出現具有指定的字型設定的範例。|
|**指令碼**|列出可用的語言指令碼，針對指定的字型。 當您選取不同的語言指令碼時，字元集的語言可用來建立多國語言的文件。|

#### <a name="to-change-the-font-of-text-on-an-image"></a>若要變更的映像上的文字的字型

下列程序是文字的如何將文字新增至 Windows 應用程式中的圖示和操作您字型的範例。

1. 建立 c + + Windows Forms 應用程式。 如需詳細資訊，請參閱 <<c0> [ 建立 Windows 應用程式專案](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5)。 *App.ico*檔案預設會新增至您的專案。

1. 在 **方案總管**，按兩下檔案*app.ico*。 [影像編輯器](../windows/image-editor-for-icons.md)隨即開啟。

1. 從**映像**功能表上，選取**工具**，然後選取**文字工具**。 **文字工具**對話方塊會隨即出現。

1. 在 [**文字工具**] 對話方塊中，輸入*c + +* 空的文字區域中。 此文字會出現在可調整大小的方塊的左角*app.ico*，請在**影像編輯器**。

1. 在 **影像編輯器**，將可調整大小的方塊拖曳到 app.ico 中心，以改善文字的可讀性。

1. 在 [**文字工具**對話方塊中，選取**字型**] 按鈕。 **文字工具字型**對話方塊會隨即出現。

1. 在 **文字工具字型**對話方塊中，選取**Times New Roman**從清單中所列的可用字型**字型**清單方塊。

1. 選取 **粗體**從清單中列出可用的字型樣式**字型樣式**清單方塊。

1. 選取  **10**從可用的點中所列的大小**大小**清單方塊。

1. 選取 [確定] 按鈕。 **文字工具字型**對話方塊會關閉，而新的字型設定將套用到您的文字。

1. 選取 [**關閉**按鈕**文字工具**] 對話方塊。 可調整您在文字周圍方塊會從消失**影像編輯器**。

### <a name="text-area"></a>文字區域

顯示文字顯示為資源的一部分。 一開始，此區域是空的。

> [!NOTE]
> 如果**透明背景**已經設定，只有文字會放入映像。 如果**不透明背景**已設定的周框，填滿[背景色彩](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)，將會放置文字的背景。 如需詳細資訊，請參閱 <<c0> [ 選擇不透明和透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。

您可以以滑鼠右鍵按一下**文字工具**對話方塊，即可存取預設的捷徑功能表，其中包含一份標準的 Windows 命令。

## <a name="to-display-or-hide-the-image-editor-toolbar"></a>若要顯示或隱藏影像編輯器工具列

因為有許多種繪圖工具可從[鍵盤](../windows/accelerator-keys-image-editor-for-icons.md)，可能會很有用隱藏**影像編輯器**工具列。

在 **檢視**功能表上，選取**工具列**然後選擇**影像編輯器**。

   > [!NOTE]
   > 這個工具列中的項目都會出現時的映像檔無法使用從目前的專案或方案不是在中開啟**影像編輯器**。 請參閱[建立圖示或其他影像](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)，如需有關將影像檔新增至您的專案資訊。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[色彩視窗](../windows/colors-window-image-editor-for-icons.md)<br/>
[編輯圖形資源](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>