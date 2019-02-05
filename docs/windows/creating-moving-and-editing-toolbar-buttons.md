---
title: 建立、 移動和編輯工具列按鈕 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.toolbar
helpviewer_keywords:
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
ms.assetid: d0f0c6c6-9d7e-42b5-a86a-7558127386e7
ms.openlocfilehash: 2a67123e444ad208eaae74a24b72288f2dbb3bdb
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742696"
---
# <a name="creating-moving-and-editing-toolbar-buttons-c"></a>建立、 移動和編輯工具列按鈕 （c + +）

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

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

請參閱下列動作：

## <a name="to-create-a-new-toolbar-button"></a>若要建立新的工具列按鈕

1. 在 [資源檢視](../windows/resource-view-window.md)展開 [資源] 資料夾 (例如*Project1.rc*)。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 依序展開**工具列**資料夾，然後選取要編輯的工具列。

1. 空白的按鈕，工具列的右端指派識別碼。 則可以藉由編輯**識別碼**中的屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)。 比方說，您可以為工具列按鈕提供相同的 ID 為功能表選項。 在此情況下，使用下拉式清單方塊來選取**識別碼**的功能表選項。

   -或-

   選取 [空白] 按鈕的工具列的右端 (在**工具列檢視**窗格)，並開始繪圖。 指派的預設按鈕的命令識別碼 (ID_BUTTON\<n >)。

您也可以複製並貼上到做為新按鈕的工具列上的映像。

## <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>若要將影像加入為按鈕的工具列

1. 在 [資源檢視](../windows/resource-view-window.md)，按兩下 [開啟] 工具列。

1. 接下來，開啟您想要新增至您的工具列影像。

   > [!NOTE]
   > 如果您在 Visual Studio 中開啟映像，即會開啟在**映像**編輯器。 您也可以開啟在其他圖形程式中的映像。

1. 從**編輯**功能表上，選擇**複製**。

1. 選取 [來源] 視窗頂端的索引標籤切換至您的工具列。

1. 從**編輯**功能表上，選擇**貼上**。

   映像會出現在工具列中，為新的按鈕。

## <a name="to-move-a-toolbar-button"></a>若要移動的工具列按鈕

在 **工具列檢視** 窗格中，拖曳您想要移到其新的位置 工具列上的按鈕。

## <a name="to-copy-buttons-from-a-toolbar"></a>若要從工具列複製按鈕

1. 按住**Ctrl**索引鍵。

1. 在 [**工具列檢視**] 窗格中，將拖曳按鈕到其新位置工具列上或位置在另一個工具列上。

## <a name="to-delete-a-toolbar-button"></a>若要刪除的工具列按鈕

選取工具列按鈕，並將它拖曳出工具列。

## <a name="to-insert-or-remove-space-between-buttons-on-a-toolbar"></a>若要插入或移除工具列按鈕之間的空間

一般情況下，若要插入按鈕之間的空白，將它們拖曳搶奪工具列上。 若要移除空格，請將它們拖曳朝向彼此。

### <a name="to-insert-a-space-before-a-button-that-isnt-followed-by-a-space"></a>若要不後接空格的按鈕之前插入空格

將按鈕拖曳至右或向下直到它重疊的下一步 按鈕的相關地球的另一端。

### <a name="to-insert-a-space-before-a-button-that-is-followed-by-a-space-and-to-keep-the-trailing-space"></a>前面插入空格 按鈕，後面接著一個空格，並保留尾端的空格

拖曳按鈕，直到右邊緣或下邊緣只會觸碰 [下一步] 按鈕，或只在其上重疊現象。

### <a name="to-insert-a-space-before-a-button-that-is-followed-by-a-space-and-close-up-that-following-space"></a>前面插入空格 按鈕，後面接著一個空格，並關閉的空白

將按鈕拖曳至右或向下直到它重疊的下一步 按鈕的相關地球的另一端。

### <a name="to-remove-a-space-between-buttons-on-a-toolbar"></a>若要移除工具列按鈕之間的空格

拖曳按鈕空間的另一端的按鈕朝著空間的某一邊，直到它重疊偶數的相關的下一步 按鈕。

   如果沒有側邊的按鈕，您所拖曳的離開的空間，而且您將按鈕拖曳多個中間時，[相鄰] 按鈕，過去**工具列**編輯器也會插入的按鈕，您是相對的一邊的空間拖曳。

## <a name="to-change-the-properties-of-a-toolbar-button"></a>若要變更工具列按鈕的屬性

1. 在 c + + 專案中，選取工具列按鈕。

1. 輸入中的新識別碼**識別碼**中的屬性[屬性視窗](/visualstudio/ide/reference/properties-window)，或使用下拉式清單選取新**識別碼**。

## <a name="requirements"></a>需求

MFC 或 ATL

## <a name="see-also"></a>另請參閱

[工具列編輯器](../windows/toolbar-editor.md)
