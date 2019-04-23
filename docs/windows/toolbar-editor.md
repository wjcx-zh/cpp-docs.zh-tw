---
title: 工具列編輯器 (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.toolbar.F1
- vc.editors.toolbar
- vc.editors.newtoolbarresource
helpviewer_keywords:
- resource editors [C++], Toolbar editor
- editors, toolbars
- toolbars [C++], editing
- Toolbar editor
- toolbars [C++], creating
- Toolbar editor [C++], creating new toolbars
- Insert Resource
- bitmaps [C++], converting to toolbars
- Toolbar editor [C++], converting bitmaps
- toolbars [C++], converting bitmaps
- New Toolbar Resource dialog box [C++]
- buttons [C++], custom toolbars
- toolbar buttons [C++], editing
- buttons
- toolbar buttons [C++], creating
- Toolbar editor [C++], creating buttons
- toolbar buttons [C++], button image
- toolbar buttons [C++], creating
- toolbar buttons (in Toolbar editor)
- toolbar buttons [C++], moving
- Toolbar editor [C++], moving buttons
- Toolbar editor [C++], copying buttons
- toolbars [C++], copying buttons
- toolbar buttons [C++], copying
- toolbar buttons [C++], deleting
- Toolbar editor [C++], deleting buttons
- Toolbar editor [C++], spacing toolbar buttons
- toolbar buttons [C++], space between buttons
- toolbar controls [MFC], command ID
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- command IDs, toolbar buttons
- size, toolbar buttons
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- status bars [C++], active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
- tool tips [C++], adding to toolbar buttons
- "\n in tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor [C++], creating tool tips
ms.assetid: aa9f0adf-60f6-4f79-ab05-bc330f15ec43
ms.openlocfilehash: 9d50561c598f17e251425972590c0663efe6e832
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038148"
---
# <a name="toolbar-editor-c"></a>工具列編輯器 (C++)

**工具列編輯器**可讓您建立工具列資源，並將點陣圖轉換成工具列資源。 **工具列編輯器**顯示的工具列和按鈕，非常類似於中完成的應用程式外觀將會使用圖形化顯示。

**工具列編輯器** 視窗會顯示兩個按鈕的影像，與相同檢視**影像編輯器**視窗。 分割列分隔的兩個窗格，您可以從側邊拖曳分隔列，以變更窗格的相對大小。 [作用中] 窗格會顯示選取框線，並將映像的兩個檢視上方是主旨工具列。

![Toolbar Editor](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")<br/>
**工具列編輯器**

**工具列編輯器**大致**影像編輯器**功能和功能表項目，圖形工具和兩者之間的點陣圖格線都相同。 中沒有功能表命令**映像**之間切換功能表**工具列編輯器**並**影像編輯器**。 如需有關使用**圖形**工具列**色彩**調色盤，或**映像**功能表上，請參閱[影像編輯器](../windows/image-editor-for-icons.md)。

您可以建立新的工具列中C++藉由轉換點陣圖的專案。 從點陣圖圖形將轉換成工具列按鈕影像。 通常，點陣圖包含數個按鈕上的映像單一的點陣圖，使用一個映像的每個按鈕。 映像可以是影像的任何大小的預設值為 16 個像素寬的高度。 您可以指定在按鈕影像的大小**新增工具列資源**當您選擇的對話方塊**工具列編輯器**從**映像**功能表時**影像編輯器**。

**新增工具列資源** 對話方塊可讓您指定您要新增工具列資源中按鈕的高度與寬度C++專案。 預設值是 16 × 15 像素。

用來建立工具列點陣圖的最大寬度為 2048，因此如果您將** 按鈕寬度**要*512*，只能有四個按鈕。 如果您將寬度設成*513*，只能有三個按鈕。

**新增工具列資源**對話方塊具有下列屬性：

|屬性|描述|
|---|---------------|
|**按鈕寬度**|提供空間讓您輸入要從一個點陣圖資源轉換成工具列資源的工具列按鈕的寬度。|
|**按鈕高度**|提供空間讓您輸入要從一個點陣圖資源轉換成工具列資源的工具列按鈕的高度。|

> [!NOTE]
> 映像會裁剪成指定的高度與寬度和色彩會調整為使用標準工具列色彩 （16 種色彩）。

根據預設，新的或空白的按鈕會顯示在工具列的右邊。 您可以編輯之前先移動此按鈕。 當您建立新的按鈕時，另一個空白的按鈕會出現 [編輯] 按鈕的右邊。 當您儲存工具列時，[空白] 按鈕不會儲存。

工具列按鈕具有下列屬性：

|屬性|描述|
|--------------|-----------------|
|**ID**|定義按鈕的識別碼。 下拉式清單提供常見**識別碼**名稱。|
|[寬度]|設定按鈕的寬度。 建議您使用 16 像素為單位。|
|[高度]|設定按鈕的高度。 一個按鈕的高度變更工具列上的所有按鈕的高度。 建議使用 15 像素為單位。|
|**提示**|定義在狀態列中顯示的訊息。 新增*\n* ，並將名稱加入**工具提示**加入工具列按鈕。 如需詳細資訊，請參閱 <<c0> [ 建立工具提示](../windows/creating-a-tool-tip-for-a-toolbar-button.md)。|

**寬度**並**高度**適用於所有按鈕。 用來建立工具列點陣圖的最大寬度為 2048，因此如果您將按鈕寬度*512*只能有四個按鈕，如果您將寬度設成*513*，只能有三個按鈕。

## <a name="how-to"></a>如何

**工具列編輯器**可讓您：

### <a name="to-create-new-toolbars"></a>若要建立新的工具列

1. 在 **資源檢視**，以滑鼠右鍵按一下您 *.rc*檔案，然後選擇**加入資源**。 如果您在現有工具列您 *.rc*檔案中，您可以以滑鼠右鍵按一下**工具列**資料夾，然後選取**插入工具列**。

1. 在 **加入資源**對話方塊中，選取**工具列**中**資源類型**清單，然後選擇**新增**。

   如果一個加號 (**+**) 旁邊會出現**工具列**資源類型，表示工具列範本可供使用。 選取加號，展開 範本清單中的，選取範本，然後選擇**新增**。

### <a name="to-convert-bitmaps-to-toolbar-resources"></a>若要將點陣圖轉換成工具列資源

1. 開啟現有的點陣圖資源中[影像編輯器](../windows/image-editor-for-icons.md)。 如果點陣圖還未在您 *.rc*檔案中，以滑鼠右鍵按一下 *.rc*檔案，然後選擇**匯入**，然後瀏覽至您想要加入的點陣圖您 *.rc*檔案，然後選取**開啟**。

1. 移至功能表**映像** > **工具列編輯器**。

   **新增工具列資源** 對話方塊隨即出現。 您可以變更圖示影像，以符合點陣圖的高度與寬度。 工具列影像即會顯示在**工具列編輯器**。

1. 若要完成轉換，將變更命令**識別碼** 按鈕使用[屬性 視窗](/visualstudio/ide/reference/properties-window)。 輸入新*識別碼*或選取**識別碼**從下拉式清單。

   > [!TIP]
   > **屬性** 視窗包含圖釘按鈕的標題列中，並選取此選項啟用或停用**自動隱藏**視窗。 若要循環瀏覽所有工具列按鈕屬性而不必重新開啟個別的屬性視窗，開啟**自動隱藏**關閉所以**屬性** 視窗會保持不動。

   您也可以藉由變更命令 Id，新的工具列上的按鈕[屬性 視窗](/visualstudio/ide/reference/properties-window)。

### <a name="to-manage-toolbar-buttons"></a>若要管理工具列按鈕

#### <a name="to-create-a-new-toolbar-button"></a>若要建立新的工具列按鈕

1. 在 [資源檢視](how-to-create-a-resource-script-file.md#create-resources)展開 [資源] 資料夾 (例如*Project1.rc*)。

1. 依序展開**工具列**資料夾，然後選取工具列來編輯，然後執行下列其中之一：

   - 空白的按鈕，工具列的右端指派識別碼。 則可以藉由編輯**識別碼**中的屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)。 比方說，您可以為工具列按鈕提供相同的 ID 為功能表選項。 在此情況下，使用下拉式清單方塊來選取**識別碼**的功能表選項。

   - 選取 [空白] 按鈕的工具列中的右端**工具列檢視**窗格，並開始繪圖。 指派的預設按鈕的命令識別碼 (ID_BUTTON\<n >)。

#### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>若要將影像加入為按鈕的工具列

1. 在 [資源檢視](how-to-create-a-resource-script-file.md#create-resources)，按兩下 [開啟] 工具列。

1. 接下來，開啟您想要新增至您的工具列影像。

   > [!NOTE]
   > 如果您在 Visual Studio 中開啟映像，即會開啟在**影像編輯器**。 您也可以開啟在其他圖形程式中的映像。

1. 移至功能表**編輯** > **複製**。

1. 選取 [來源] 視窗頂端的索引標籤切換至您的工具列。

1. 移至功能表**編輯** > **貼上**。

   映像會出現在工具列中，為新的按鈕。

#### <a name="to-move-a-toolbar-button"></a>若要移動的工具列按鈕

在 **工具列檢視** 窗格中，拖曳您想要移到其新的位置 工具列上的按鈕。

- 若要從工具列複製按鈕，按住**Ctrl**機碼並在**工具列檢視** 窗格中，將拖曳按鈕到其新位置工具列上或位置在另一個工具列上。

- 若要刪除的工具列按鈕，選取工具列按鈕，並將它拖曳出工具列。

- 若要插入或移除工具列按鈕之間的空間，請將它們拖曳以外的位置，或針對另一個工具列上。

|動作|步驟|
|------|------|
|若要不後接空格的按鈕之前插入空格|將按鈕拖曳至右或向下直到它重疊的下一步 按鈕的相關地球的另一端。|
|前面插入空格 按鈕，後面接著一個空格，並保留尾端的空格|拖曳按鈕，直到右邊緣或下邊緣只會觸碰 [下一步] 按鈕，或只在其上重疊現象。|
|前面插入空格 按鈕，後面接著一個空格，並關閉的空白|將按鈕拖曳至右或向下直到它重疊的下一步 按鈕的相關地球的另一端。|
|若要移除工具列按鈕之間的空格|拖曳按鈕空間的另一端的按鈕朝著空間的某一邊，直到它重疊偶數的相關的下一步 按鈕。|

> [!NOTE]
> 如果沒有空間旁邊的按鈕，您所拖曳的以外的位置，而且您將按鈕拖曳多個中間時，[相鄰] 按鈕，過去**工具列編輯器**插入見所拖曳的按鈕上的另一端的空間。

#### <a name="to-change-the-properties-of-a-toolbar-button"></a>若要變更工具列按鈕的屬性

1. 在C++專案中，選取工具列按鈕。

1. 輸入中的新識別碼**識別碼**中的屬性[屬性視窗](/visualstudio/ide/reference/properties-window)，或使用下拉式清單選取新**識別碼**。

#### <a name="to-create-a-tool-tip-for-a-toolbar-button"></a>若要建立工具列按鈕的工具提示

1. 選取工具列按鈕。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，請在**提示**欄位中，新增按鈕的狀態列和訊息之後的描述、 新增`\n`和工具提示名稱。

例如，若要查看的工具提示**列印**按鈕**WordPad**:

1. 開啟**WordPad**。

1. 將滑鼠指標停留**列印**工具列按鈕，請注意 word`Print`現在浮動在滑鼠指標。

1. 查看底部的狀態列**WordPad**視窗，並請注意，現在會顯示文字`Prints the active document`。

`Print` 為工具提示名稱和`Prints the active document`是針對 [狀態] 列按鈕的描述。

如果您想使用此效果**工具列編輯器**，將**提示**屬性設`Prints the active document\nPrint`。

## <a name="requirements"></a>需求

MFC 或 ATL

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)
<!--
[Menus and Other Resources](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)<br/>
[Toolbar Button Properties](../windows/toolbar-button-properties.md)<br/>-->
