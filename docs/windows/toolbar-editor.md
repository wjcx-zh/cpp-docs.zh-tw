---
title: 工具列編輯器（C++）
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
ms.openlocfilehash: 72c42a06da8276d118c6c204f838ed4b31d142b9
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "69514686"
---
# <a name="toolbar-editor-c"></a>工具列編輯器（C++）

**工具列編輯器**可讓您建立工具列資源，並將點陣圖轉換成工具列資源。 **工具列編輯器**會使用圖形顯示來顯示工具列和按鈕，與它們在完成的應用程式中的外觀相似。

[**工具列編輯器**] 視窗會顯示按鈕影像的兩個視圖，與 [**影像編輯器**] 視窗相同。 分割列會分隔兩個窗格，而且您可以從側邊拖曳分割列，以變更窗格的相對大小。 [使用中] 窗格會顯示選取範圍框線，而影像的兩個視圖上方則是 [主旨] 工具列。

![工具列編輯器](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")<br/>
**工具列編輯器**

**工具列編輯器**類似于**影像編輯器**的功能，兩者之間的功能表項目、圖形工具和點陣圖方格都相同。 [**影像**] 功能表中有一個功能表命令，可在 [**工具列編輯器**] 和 [**影像編輯器**] 之間切換。 如需使用 [**圖形**] 工具列、[**色彩**] 調色板或 [**影像**] 功能表的詳細資訊，請參閱[影像編輯器](../windows/image-editor-for-icons.md)。

您可以藉由轉換點陣圖，在C++專案中建立新的工具列。 點陣圖中的圖形會轉換成工具列的按鈕影像。 點陣圖通常會在單一點陣圖上包含數個按鈕影像，每個按鈕都有一個影像。 影像可以是任何大小，預設值為16圖元寬和影像高度。 當您在**影像編輯器**中，從 [**影像**] 功能表選擇 [**工具列編輯器**] 時，可以在 [**新工具列資源**] 對話方塊中指定按鈕影像的大小。

[**新增工具列資源**] 對話方塊可讓您指定要加入至C++專案中的工具列資源之按鈕的寬度和高度。 預設值為16×15圖元。

用來建立工具列的點陣圖寬度上限為2048，因此如果您將**按鈕寬度**設定為*512*，則只能有四個按鈕。 如果您將 [寬度] 設定為*513*，則只能有三個按鈕。

[**新增工具列資源**] 對話方塊具有下列屬性：

|屬性|描述|
|---|---------------|
|**按鈕寬度**|提供空間，讓您輸入要從點陣圖資源轉換為工具列資源的工具列按鈕寬度。|
|**按鈕高度**|提供空間讓您輸入從點陣圖資源轉換為工具列資源的工具列按鈕高度。|

> [!NOTE]
> 影像會裁剪成指定的寬度和高度，而色彩則會調整為使用標準工具列色彩（16色）。

根據預設，工具列的右端會顯示新的或空白按鈕。 您可以在編輯之前先移動此按鈕。 當您建立新的按鈕時，[已編輯] 按鈕的右邊會出現另一個空白按鈕。 當您儲存工具列時，不會儲存空白按鈕。

工具列按鈕具有下列屬性：

|屬性|描述|
|--------------|-----------------|
|**ID**|定義按鈕的識別碼。 下拉式清單會提供通用的**識別碼**名稱。|
|[寬度]|設定按鈕的寬度。 建議使用16圖元。|
|[高度]|設定按鈕的高度。 一個按鈕的高度會變更工具列上所有按鈕的高度。 建議使用15圖元。|
|**提示**|定義狀態列中顯示的訊息。 新增 *\n*和名稱會將**工具提示**新增至該工具列按鈕。 如需詳細資訊，請參閱[建立工具提示](../windows/creating-a-tool-tip-for-a-toolbar-button.md)。|

**寬度**和**高度**適用于所有按鈕。 用來建立工具列的點陣圖寬度上限為2048，因此如果您將按鈕寬度設定為*512*，則只能有四個按鈕，如果您將寬度設定為*513*，則只能有三個按鈕。

## <a name="how-to"></a>如何

**工具列編輯器**可讓您：

### <a name="to-create-new-toolbars"></a>若要建立新的工具列

1. 在**資源檢視**中，以滑鼠右鍵按一下 *.rc*檔，然後選擇 [**新增資源**]。 如果您的 *.rc*檔中有現有的工具列，您可以在 [**工具列**] 資料夾上按一下滑鼠右鍵，然後選取 [**插入工具列**]。

1. 在 [**新增資源**] 對話方塊中，選取 [**資源類型**] 清單中的 [**工具列**]，然後選擇 [**新增**]。

   如果 [**工具列**] 資源類型旁出現一個加號（ **+** ），表示工具列範本可以使用。 選取加號展開範本清單，選取範本，然後選擇 [**新增**]。

### <a name="to-convert-bitmaps-to-toolbar-resources"></a>將點陣圖轉換成工具列資源

1. 在[影像編輯器](../windows/image-editor-for-icons.md)中開啟現有的點陣圖資源。 如果點陣圖還不在 *.rc*檔中，請以滑鼠右鍵按一下 *.rc*檔並選擇 [匯**入**]，然後流覽至您要加入 *.rc*檔的點陣圖，再選取 [**開啟**]。

1. 移至 功能表 **影像** > **工具列編輯器**。

   [**新工具列資源**] 對話方塊隨即出現。 您可以變更圖示影像的寬度和高度，使其符合點陣圖。 工具列影像隨即顯示在**工具列編輯器**中。

1. 若要完成轉換，請使用[屬性視窗](/visualstudio/ide/reference/properties-window)變更按鈕的命令**ID** 。 輸入新的*識別碼*，或從下拉式清單中選取**識別碼**。

   > [!TIP]
   > [**屬性**] 視窗會在標題列中包含圖釘按鈕，並選取這會啟用或停用視窗的 [**自動隱藏**]。 若要迴圈流覽所有的工具列按鈕屬性，而不需要重新開啟個別的屬性視窗，請開啟 [**自動隱藏**]，讓 [**屬性**] 視窗保持固定。

   您也可以使用 [[屬性視窗](/visualstudio/ide/reference/properties-window)]，變更新工具列上按鈕的命令識別碼。

### <a name="to-manage-toolbar-buttons"></a>管理工具列按鈕

#### <a name="to-create-a-new-toolbar-button"></a>若要建立新的工具列按鈕

1. 在[資源檢視](how-to-create-a-resource-script-file.md#create-resources)展開 [資源] 資料夾（例如， *Project1*）。

1. 展開 [**工具列**] 資料夾並選取要編輯的工具列，然後執行下列其中一項動作：

   - 將識別碼指派給工具列右端的空白按鈕。 您可以在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)中編輯**ID**屬性來執行此動作。 例如，您可能會想要為工具列按鈕提供與功能表選項相同的識別碼。 在此情況下，請使用下拉式清單方塊來選取功能表選項的**識別碼**。

   - 選取**工具列 [流覽**] 窗格中工具列右端的空白按鈕，然後開始繪製。 指派預設按鈕命令識別碼（ID_BUTTON\<n >）。

#### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>將影像新增至工具列做為按鈕

1. 在[資源檢視](how-to-create-a-resource-script-file.md#create-resources)中，按兩下工具列以開啟它。

1. 接下來，開啟您想要新增至工具列的影像。

   > [!NOTE]
   > 如果您在 Visual Studio 中開啟影像，它會在**影像編輯器**中開啟。 您也可以在其他圖形程式中開啟影像。

1. 移至功能表 **編輯** > **複製**。

1. 選取 [來源] 視窗頂端的 [] 索引標籤，切換至您的工具列。

1. 移至功能表 [**編輯** > **貼**上]。

   影像會在工具列上顯示為 [新增] 按鈕。

#### <a name="to-move-a-toolbar-button"></a>移動工具列按鈕

在 [**工具列] 視圖**窗格中，將您想要移動的按鈕拖曳至工具列上的新位置。

- 若要從工具列複製按鈕，請按住**Ctrl**鍵，然後在工具列的 [**視圖**] 窗格中，將按鈕拖曳至工具列上的新位置或另一個工具列上的位置。

- 若要刪除工具列按鈕，請選取工具列按鈕，並將它拖曳至工具列。

- 若要在工具列上的按鈕之間插入或移除空格，請將它們拖曳到工具列上，或移到另一個工具列上。

|動作|步驟|
|------|------|
|在後面加上空格的按鈕前面插入空格|將按鈕向右或向下拖曳，直到其與 [下一步] 按鈕重迭一半為止。|
|在後面加上空格並保留尾端空格的按鈕前面插入空格|拖曳按鈕，直到右邊或下邊緣只觸及 [下一步] 按鈕，或只是重迭它。|
|在後面加上空格的按鈕前面插入空格，並關閉後面的空格|將按鈕向右或向下拖曳，直到其與 [下一步] 按鈕重迭一半為止。|
|移除工具列按鈕之間的空格|將 [按鈕] 拖曳到空間另一端的按鈕，直到與 [下一步] 按鈕重迭一半為止。|

> [!NOTE]
> 如果您要拖曳的按鈕旁邊沒有任何空間，而您將按鈕拖曳到相鄰按鈕的一半以上，**工具列編輯器**會在您要拖曳的按鈕旁邊插入一個空格。

#### <a name="to-change-the-properties-of-a-toolbar-button"></a>變更工具列按鈕的屬性

1. 在C++專案中，選取 [工具列] 按鈕。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)的 [**識別碼**] 屬性中輸入新的識別碼，或使用下拉式清單來選取新的**識別碼**。

#### <a name="to-create-a-tool-tip-for-a-toolbar-button"></a>建立工具列按鈕的工具提示

1. 選取工具列按鈕。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)的 [**提示**] 欄位中，新增狀態列的 [描述] 和 [在訊息之後加入 `\n`] 和 [工具提示名稱]。

例如，若要查看**WordPad**中 [**列印**] 按鈕的工具提示：

1. 開啟 [ **WordPad**]。

1. 將滑鼠指標暫留在 [**列印**] 工具列按鈕上，並注意 [`Print`] 這個字現在會浮動在滑鼠指標之下。

1. 查看 [ **WordPad** ] 視窗底部的狀態列，並注意它現在會顯示 `Prints the active document`的文字。

`Print` 是工具提示名稱，`Prints the active document` 則是狀態列的按鈕描述。

如果您想要使用**工具列編輯器**來進行這種效果，請將 [**提示**] 屬性設定為 [`Prints the active document\nPrint`]。

## <a name="requirements"></a>需求

MFC 或 ATL

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)
[功能表和其他資源](/windows/win32/menurc/resources)<br/>
[工具列按鈕屬性](../windows/toolbar-button-properties.md)<br/>
