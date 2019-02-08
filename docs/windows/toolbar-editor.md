---
title: 工具列編輯器 （c + +）
ms.date: 11/04/2016
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
ms.openlocfilehash: 61b4d3ba6fc70e78c6f794528822eb66fb94de7e
ms.sourcegitcommit: 5a7dbd640376e13379f5d5b2cf66c4842e5e737b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55905780"
---
# <a name="toolbar-editor-c"></a>工具列編輯器 （c + +）

**工具列**編輯器可讓您建立 c + + 工具列資源，並將點陣圖轉換成工具列資源。 **工具列**編輯器来顯示的工具列和按鈕，非常類似於中完成的應用程式外觀將使用的圖形化顯示。

**工具列**編輯器 視窗會顯示兩個按鈕的影像，影像編輯器 視窗相同檢視。 這兩個窗格會以分隔列區隔。 您可隨意地拖曳分隔列，以變更窗格的相對大小。 現用窗格會顯示選取框線。 影像的兩個檢視上方是主旨工具列。

![工具列編輯器](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")工具列編輯器

** 工具列**編輯器是類似**映像**編輯器的功能。 功能表項目、 圖形工具和點陣圖格線都與相同**映像**編輯器。 沒有功能表命令**映像**功能表可讓您切換**工具列**編輯器與**映像**編輯器。 如需有關使用**圖形**工具列**色彩**調色盤，或**映像**功能表上，請參閱[影像編輯器](../windows/image-editor-for-icons.md)。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

具有**工具列**編輯器，您可以：

## <a name="create-new-toolbars"></a>建立新的工具列

1. 在  **Resource**檢視，以滑鼠右鍵按一下.rc 檔，然後選擇**加入資源**從捷徑功能表。 (如果您將現有工具列在.rc 檔時，您可以直接以滑鼠右鍵按一下 **工具列**資料夾，然後選取**插入工具列**從捷徑功能表。)

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 在 **加入資源**對話方塊中，選取**工具列**中**資源類型**清單，然後選擇**新增**。

   如果一個加號 (**+**) 旁邊會出現**工具列**資源類型，表示工具列範本可供使用。 選取加號，展開 範本清單中的，選取範本，然後選擇**新增**。

## <a name="convert-bitmaps-to-toolbar-resources"></a>將點陣圖轉換成工具列資源

轉換點陣圖，您可以在 c + + 專案中建立新的工具列。 從點陣圖圖形將轉換成工具列按鈕影像。 通常，點陣圖包含數個按鈕上的映像單一的點陣圖，使用一個映像的每個按鈕。 映像可以是影像的任何大小的預設值為 16 個像素寬的高度。 您可以指定在按鈕影像的大小**新增工具列資源**當您選擇的對話方塊**工具列編輯器**從**映像**影像編輯器中的功能表。

**新增工具列資源**對話方塊可讓您指定您要新增工具列資源在 c + + 專案中的按鈕的高度與寬度。 預設值是 16 × 15 像素。

用來建立工具列點陣圖具有最大寬度為 2048年。 因此，如果您設定** 按鈕寬度**設為 512，您只能有四個按鈕。 如果您將寬度設成 513，您只能有三個按鈕。

對話方塊具有下列屬性：

|屬性|描述|
|---|---|
|**按鈕寬度**|提供空間讓您輸入要從一個點陣圖資源轉換成工具列資源的工具列按鈕的寬度。 映像會裁剪成指定的高度與寬度和色彩會調整為使用標準工具列色彩 （16 種色彩）。|
|**按鈕高度**|提供空間讓您輸入要從一個點陣圖資源轉換成工具列資源的工具列按鈕的高度。 映像會裁剪成指定的高度與寬度和色彩會調整為使用標準工具列色彩 （16 種色彩）。|

### <a name="to-convert-bitmaps-to-a-toolbar"></a>若要將點陣圖轉換成工具列

1. 開啟現有的點陣圖資源中[影像編輯器](../windows/image-editor-for-icons.md)。 (如果點陣圖沒有.rc 檔，以滑鼠右鍵按一下.rc 檔，請選擇**匯入**從捷徑功能表中，瀏覽至您想要新增至您的.rc 檔，點陣圖，然後選取**開啟**。)

1. 從**映像**功能表上，選擇**工具列編輯器**。

   **新增工具列資源** 對話方塊隨即出現。 您可以變更圖示影像，以符合點陣圖的高度與寬度。 工具列影像即會顯示在工具列編輯器中。

1. 若要完成轉換，將變更命令**識別碼** 按鈕使用[屬性 視窗](/visualstudio/ide/reference/properties-window)。 輸入新**識別碼**或選取**識別碼**從下拉式清單。

   > [!TIP]
   > **屬性**視窗包含標題列中的圖釘按鈕。 選取此按鈕啟用或停用**自動隱藏**視窗。 若要快速循環顯示所有工具列按鈕屬性而不必重新開啟個別的屬性視窗，開啟**自動隱藏**關閉所以**屬性** 視窗會保持不動。

您也可以藉由變更命令 Id，新的工具列上的按鈕[屬性 視窗](/visualstudio/ide/reference/properties-window)。

## <a name="create-move-and-edit-toolbar-buttons"></a>建立、移動和編輯工具列按鈕

您可以輕鬆地建立、 移動、 複製和編輯工具列按鈕。

根據預設，新的或空白的按鈕會顯示在工具列的右邊。 您可以編輯之前先移動此按鈕。 當您建立新的按鈕時，另一個空白的按鈕會出現 [編輯] 按鈕的右邊。 當您儲存工具列時，[空白] 按鈕不會儲存。

工具列按鈕的屬性如下：

|屬性|描述|
|--------------|-----------------|
|**ID**|定義按鈕的識別碼。 下拉式清單提供常見**識別碼**名稱。|
|[寬度]|設定按鈕的寬度。 建議您使用 16 像素為單位。|
|[高度]|設定按鈕的高度。 一個按鈕的高度變更工具列上的所有按鈕的高度。 建議使用 15 像素為單位。|
|**提示**|定義在狀態列中顯示的訊息。 加入 \n 和名稱加入至該工具列按鈕的工具提示。 如需詳細資訊，請參閱 <<c0> [ 建立工具提示](../windows/creating-a-tool-tip-for-a-toolbar-button.md)。|

**寬度**並**高度**適用於所有按鈕。 用來建立工具列點陣圖具有最大寬度為 2048年。 因此如果您可以設定按鈕的寬度設為 512，只能有四個按鈕，並將寬度設成 513，如果您只可以有三個按鈕。

請參閱下列動作：

### <a name="to-create-a-new-toolbar-button"></a>若要建立新的工具列按鈕

1. 在 [資源檢視](../windows/resource-view-window.md)展開 [資源] 資料夾 (例如*Project1.rc*)。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 依序展開**工具列**資料夾，然後選取要編輯的工具列。

1. 空白的按鈕，工具列的右端指派識別碼。 則可以藉由編輯**識別碼**中的屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)。 比方說，您可以為工具列按鈕提供相同的 ID 為功能表選項。 在此情況下，使用下拉式清單方塊來選取**識別碼**的功能表選項。

   -或-

   選取 [空白] 按鈕的工具列的右端 (在**工具列檢視**窗格)，並開始繪圖。 指派的預設按鈕的命令識別碼 (ID_BUTTON\<n >)。

您也可以複製並貼上到做為新按鈕的工具列上的映像。

### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>若要將影像加入為按鈕的工具列

1. 在 [資源檢視](../windows/resource-view-window.md)，按兩下 [開啟] 工具列。

1. 接下來，開啟您想要新增至您的工具列影像。

   > [!NOTE]
   > 如果您在 Visual Studio 中開啟映像，即會開啟在**映像**編輯器。 您也可以開啟在其他圖形程式中的映像。

1. 從**編輯**功能表上，選擇**複製**。

1. 選取 [來源] 視窗頂端的索引標籤切換至您的工具列。

1. 從**編輯**功能表上，選擇**貼上**。

   映像會出現在工具列中，為新的按鈕。

### <a name="to-move-a-toolbar-button"></a>若要移動的工具列按鈕

在 **工具列檢視** 窗格中，拖曳您想要移到其新的位置 工具列上的按鈕。

### <a name="to-copy-buttons-from-a-toolbar"></a>若要從工具列複製按鈕

1. 按住**Ctrl**索引鍵。

1. 在 [**工具列檢視**] 窗格中，將拖曳按鈕到其新位置工具列上或位置在另一個工具列上。

### <a name="to-delete-a-toolbar-button"></a>若要刪除的工具列按鈕

選取工具列按鈕，並將它拖曳出工具列。

### <a name="to-insert-or-remove-space-between-buttons-on-a-toolbar"></a>若要插入或移除工具列按鈕之間的空間

一般情況下，若要插入按鈕之間的空白，將它們拖曳搶奪工具列上。 若要移除空格，請將它們拖曳朝向彼此。

|動作|步驟|
|------|------|
|若要不後接空格的按鈕之前插入空格|將按鈕拖曳至右或向下直到它重疊的下一步 按鈕的相關地球的另一端。|
|前面插入空格 按鈕，後面接著一個空格，並保留尾端的空格|拖曳按鈕，直到右邊緣或下邊緣只會觸碰 [下一步] 按鈕，或只在其上重疊現象。|
|前面插入空格 按鈕，後面接著一個空格，並關閉的空白|將按鈕拖曳至右或向下直到它重疊的下一步 按鈕的相關地球的另一端。|
|若要移除工具列按鈕之間的空格|拖曳按鈕空間的另一端的按鈕朝著空間的某一邊，直到它重疊偶數的相關的下一步 按鈕。|

> [!NOTE]
> 如果沒有側邊的按鈕，您所拖曳的離開的空間，而且您將按鈕拖曳多個中間時，[相鄰] 按鈕，過去**工具列**編輯器也會插入的按鈕，您是相對的一邊的空間拖曳。

### <a name="to-change-the-properties-of-a-toolbar-button"></a>若要變更工具列按鈕的屬性

1. 在 c + + 專案中，選取工具列按鈕。

1. 輸入中的新識別碼**識別碼**中的屬性[屬性視窗](/visualstudio/ide/reference/properties-window)，或使用下拉式清單選取新**識別碼**。

### <a name="to-create-a-tool-tip-for-a-toolbar-button"></a>若要建立工具列按鈕的工具提示

1. 選取工具列按鈕。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，請在**提示**屬性欄位中，新增按鈕，[狀態] 列，在訊息之後的描述，並新增`\n`和工具提示名稱。

工具提示的常見範例是**列印**按鈕**WordPad**:

1. 開啟**WordPad**。

1. 將滑鼠指標停留**列印**工具列按鈕。

1. 請注意，這個字`Print`現在浮動在滑鼠指標。

1. 查看 狀態 列 (在底部**WordPad**  視窗)-請注意現在會顯示文字`Prints the active document`。

`Print`中**步驟 3**是 「 工具提示名稱 」，而`Prints the active document`從**步驟 4** "的描述 [狀態] 列的按鈕。 」

如果您想使用此效果 **工具列**編輯器 」 中，您將**提示**屬性設`Prints the active document\nPrint`。

> [!NOTE]
> 您可以編輯的提示文字使用[屬性 視窗](/visualstudio/ide/reference/properties-window)。

## <a name="requirements"></a>需求

MFC 或 ATL

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)<br/>
[功能表與其他資源](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)<br/>
[工具列按鈕屬性](../windows/toolbar-button-properties.md)<br/>
