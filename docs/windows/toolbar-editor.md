---
title: " (c + +) 的工具列編輯器"
description: 使用 Visual Studio 工具列編輯器來建立工具列資源，並將點陣圖轉換成工具列資源。
ms.date: 09/26/2020
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
ms.openlocfilehash: 042bfafb1e55d45145306a8c388e1e3559fa9a33
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413797"
---
# <a name="toolbar-editor-c"></a> (c + +) 的工具列編輯器

**工具列編輯器**可讓您建立工具列資源，並將點陣圖轉換成工具列資源。 **工具列編輯器**會使用圖形顯示。 它會顯示類似于在完成的應用程式中查看的工具列和按鈕。

[ **工具列編輯器** ] 視窗會顯示按鈕影像的兩個視圖，與 [ **影像編輯器** ] 視窗相同。 這兩個窗格會以分隔列區隔。 若要變更窗格的相對大小，您可以從側邊拖曳分割列。 [使用中] 窗格會顯示選取框線，而影像的兩個視圖上方則是 [主旨] 工具列。

![工具列編輯器](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")<br/>
**工具列編輯器**

**工具列編輯器**與功能中的**影像編輯器**類似。 兩者之間的功能表項目、圖形工具和點陣圖方格相同。 [ **影像** ] 功能表中有一個功能表命令，可以在 [ **工具列編輯器** ] 和 [ **影像編輯器**] 之間切換。 如需使用 [ **圖形** ] 工具列、[ **色彩** 選擇區] 或 [ **影像** ] 功能表的詳細資訊，請參閱 [影像編輯器](../windows/image-editor-for-icons.md)。

您可以藉由轉換點陣圖，在 c + + 專案中建立新的工具列。 點陣圖中的圖形會轉換成工具列的按鈕影像。 點陣圖通常會在單一點陣圖上包含數個按鈕影像，每個按鈕都有一個影像。 影像可以是任何大小，因為預設值為16圖元寬和影像的高度。 您可以在 [ **新增工具列資源** ] 對話方塊中，指定按鈕影像的大小。 若要指定大小，請在**影像編輯器**中，從 [**影像**] 功能表選擇 [**工具列編輯器**]。

[ **新增工具列資源** ] 對話方塊可讓您指定要加入至 c + + 專案中工具列資源之按鈕的寬度和高度。 預設值為16×15圖元。

用來建立工具列的點陣圖寬度上限為2048。 如果您將 **按鈕寬度** 設定為 *512*，則只能有四個按鈕。 而且，如果您將寬度設定為 *513*，則只能有三個按鈕。

[ **新增工具列資源** ] 對話方塊具有下列屬性：

|屬性|描述|
|---|---------------|
|**按鈕寬度**|提供空間，讓您輸入要從點陣圖資源轉換成工具列資源之工具列按鈕的寬度。|
|**按鈕高度**|提供空間讓您輸入從點陣圖資源轉換成工具列資源之工具列按鈕的高度。|

> [!NOTE]
> 影像會裁剪成指定的寬度和高度，而色彩則會調整為使用標準工具列色彩 (16 色) 。

依預設，工具列會在工具列的右端顯示新的或空白按鈕。 您可以先移動這個按鈕，再進行編輯。 當您建立新按鈕時，[編輯] 按鈕的右邊會出現另一個空白按鈕。 當您儲存工具列時，不會儲存空白按鈕。

工具列按鈕具有下列屬性：

|屬性|描述|
|--------------|-----------------|
|**識別碼**|定義按鈕的識別碼。 下拉式清單提供常見的 **識別碼** 名稱。|
|**寬度**|設定按鈕的寬度。 建議使用16圖元。|
|**高度**|設定按鈕的高度。 其中一個按鈕的高度會變更工具列上所有按鈕的高度。 建議使用15圖元。|
|**提示**|定義狀態列中顯示的訊息。 新增 *\n* 和名稱會將 **工具提示** 新增至該工具列按鈕。 如需詳細資訊，請參閱 [建立工具列按鈕的工具提示](#to-create-a-tool-tip-for-a-toolbar-button)。|

**寬度** 和 **高度** 適用于所有按鈕。 用來建立工具列的點陣圖寬度上限為2048。 這表示，如果您將按鈕寬度設定為 *512*，則只能有四個按鈕。 如果您將寬度設定為 *513*，則只能有三個按鈕。

## <a name="how-to"></a>作法

**工具列編輯器**可讓您：

### <a name="to-create-new-toolbars"></a>建立新的工具列

1. 在 **資源檢視**中，以滑鼠右鍵按一下 *.rc* 檔，然後選擇 [ **加入資源**]。 如果 *.rc* 檔中有現有的工具列，您可以用滑鼠右鍵按一下 **工具列** 資料夾，然後選取 [ **插入工具列**]。

1. 在 [**新增資源**] 對話方塊中，選取 [**資源類型**] 清單中的 [**工具列**]，然後選擇 [**新增**]。

   如果 [加號] (**+**) 出現在 **工具列** 資源類型的旁邊，則表示工具列範本可以使用。 選取加號展開範本清單、選取範本，然後選擇 [ **新增**]。

### <a name="to-convert-bitmaps-to-toolbar-resources"></a>將點陣圖轉換成工具列資源

1. 在 [影像編輯器](../windows/image-editor-for-icons.md)中開啟現有的點陣圖資源。 如果該點陣圖尚未存在 *.rc* 檔中，請以滑鼠右鍵按一下 *.rc* 檔，然後選擇 [匯 **入**]。 然後，流覽至您要新增至 *.rc* 檔的點陣圖，然後選取 [ **開啟**]。

1. 移至 [功能表**影像**]  >  **工具列編輯器**。

   [ **新增工具列資源** ] 對話方塊隨即出現。 您可以變更圖示影像的寬度和高度，以符合點陣圖。 工具列影像接著會顯示在 **工具列編輯器**中。

1. 若要完成轉換，請使用[屬性視窗](/visualstudio/ide/reference/properties-window)來變更按鈕的命令**識別碼**。 輸入新的 *識別碼* ，或從下拉式清單中選取 **識別碼** 。

   > [!TIP]
   > [ **屬性** ] 視窗會在標題列中包含圖釘按鈕，並選取此按鈕可啟用或停用視窗的 **自動隱藏** 。 若要迴圈流覽所有工具列按鈕屬性，而不需要重新開啟個別的屬性視窗，請將 **自動隱藏** 關閉，讓 [ **屬性** ] 視窗維持在靜止狀態。

   您也可以使用 [屬性視窗](/visualstudio/ide/reference/properties-window)，在新工具列上變更按鈕的命令識別碼。

### <a name="to-manage-toolbar-buttons"></a>管理工具列按鈕

#### <a name="to-create-a-new-toolbar-button"></a>建立新的工具列按鈕

1. 在 [資源檢視](how-to-create-a-resource-script-file.md#create-resources) 展開資源資料夾 (例如， *Project1 .rc*) 。

1. 展開 **工具列** 資料夾並選取要編輯的工具列，然後選取下列其中一項：

   - 將識別碼指派給工具列右端的空白按鈕。 您可以在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)中編輯 [**識別碼**] 屬性來完成這項作業。 例如，您可能會想要為工具列按鈕提供與功能表選項相同的識別碼。 在此情況下，請使用下拉式清單方塊來選取功能表選項的 **識別碼** 。

   - 在工具列的 [ **視圖** ] 窗格中，選取工具列右邊的空白按鈕，然後開始繪製。  (ID_BUTTON) 指派預設按鈕命令識別碼 \<n> 。

#### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>將影像新增至工具列作為按鈕

1. 在 [資源檢視](how-to-create-a-resource-script-file.md#create-resources)中，按兩下工具列以開啟它。

1. 接下來，開啟您想要新增至工具列的影像。

   > [!NOTE]
   > 如果您在 Visual Studio 中開啟影像，它就會在 **影像編輯器**中開啟。 您也可以在其他圖形程式中開啟影像。

1. 移至功能表**編輯**  >  **複製**。

1. 在來源視窗頂端選取其索引標籤，以切換至您的工具列。

1. 移至功能表**編輯**  >  **貼**上。

   影像會以新按鈕的形式出現在工具列上。

#### <a name="to-move-a-toolbar-button"></a>移動工具列按鈕

在 **工具列視圖** 窗格中，將您要移動的按鈕拖曳至工具列上的新位置。

- 若要從工具列複製按鈕，請按住 **Ctrl** 鍵。 在工具列的 [ **視圖** ] 窗格中，將按鈕拖曳至工具列上的新位置。 或者，將它拖曳到另一個工具列上的某個位置。

- 若要刪除工具列按鈕，請選取工具列按鈕，然後將它拖曳到工具列上。

- 若要在工具列上的按鈕之間插入或移除空格，請在工具列上將它們拖曳到彼此以外的位置。

|動作|步驟|
|------|------|
|在不接空格的按鈕之前插入空格|將按鈕向右或向下拖曳，直到它重迭 [下一步] 按鈕的一半。|
|在後面加上空格並保留尾端空格的按鈕之前插入空格|拖曳按鈕，直到右邊或下邊緣只觸及 [下一步] 按鈕，或只是重迭。|
|在後面加上空格的按鈕之前插入空格，並在後面加上空格|將按鈕向右或向下拖曳，直到它重迭 [下一步] 按鈕的一半。|
|移除工具列上按鈕之間的空格|選取空間一端的按鈕。 將它拖曳到空間另一端的按鈕，直到它與 [下一步] 按鈕重迭為止。|

> [!NOTE]
> 如果您要拖曳的按鈕旁沒有任何空間，而您將按鈕拖曳到相鄰按鈕的正上方， **工具列編輯器** 會在您要拖曳之按鈕的另一端插入一個空格。

#### <a name="to-change-the-properties-of-a-toolbar-button"></a>變更工具列按鈕的屬性

1. 在 c + + 專案中，選取工具列按鈕。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)的 [**識別碼**] 屬性中輸入新的識別碼，或使用下拉式清單來選取新的**識別碼**。

#### <a name="to-create-a-tool-tip-for-a-toolbar-button"></a>建立工具列按鈕的工具提示

1. 選取工具列按鈕。

1. 在 [ [屬性] 視窗](/visualstudio/ide/reference/properties-window)的 [ **提示** ] 欄位中，加入狀態列之按鈕的描述，以及訊息之後的 [新增] `\n` 和 [工具提示名稱]。

例如，若要查看**WordPad**中 [**列印**] 按鈕的工具提示：

1. 開啟 **WordPad**。

1. 將滑鼠指標暫留在 [ **列印** ] 工具列按鈕上方，並注意現在這個字 `Print` 是浮動在滑鼠指標下。

1. 查看 **WordPad** 視窗底部的狀態列，並注意它現在會顯示文字 `Prints the active document` 。

`Print` 是工具提示名稱，而且 `Prints the active document` 是狀態列的按鈕描述。

如果您想要使用 **工具列編輯器**來產生此效果，請將 [ **提示** ] 屬性設定為 `Prints the active document\nPrint` 。

## <a name="requirements"></a>規格需求

MFC 或 ATL

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)\
[功能表和其他資源](/windows/win32/menurc/resources)
