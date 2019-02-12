---
title: HOW TO：管理資源 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
- vc.resvw.resource.changing
- vb.xmldesigner.data
- vs.resvw.resource.importing
- vc.resvw.resource.importing
helpviewer_keywords:
- resources [C++], moving between files
- resources [C++], copying
- resource files [C++], copying or moving resources between
- resource files [C++], tiling
- .rc files [C++], copying resources between
- rc files [C++], copying resources between
- Language property [C++]
- .resx files [C++], editing
- resource files [C++], editing
- resx files [C++], editing
- resources [C++], exporting
- graphics [C++], exporting
- graphics [C++], importing
- resources [C++], importing
- bitmaps [C++], importing and exporting
- toolbars [C++], importing
- images [C++], importing
- toolbars [C++], exporting
- cursors [C++], importing and exporting
- images [C++], exporting
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
ms.openlocfilehash: e8b976f974e397b8012ebf59ede08ee64f4f7191
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150788"
---
# <a name="how-to-manage-resources-c"></a>HOW TO：管理資源 （c + +）

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="to-copy-resources"></a>若要複製資源

您可以從一個檔案複製的資源，到另一個，而不需要變更它們，或者您可以複製它時變更其語言或條件的資源。

您可以輕鬆地將複製資源從現有的資源或可執行檔目前的資源檔。 若要複製的資源，您開啟這兩個同時包含資源的檔案並將項目從一個檔案拖曳到另一個或複製並貼兩個檔案之間。 這個方法適用於資源指令碼 (.rc) 檔和資源範本 (.rct) 檔，以及為可執行檔 (.exe) 檔案。

> [!NOTE]
> Visual c + + 包含您可以使用自己的應用程式中的範例資源檔案。 如需詳細資訊，請參閱[美工圖案：通用資源](https://github.com/Microsoft/VCSamples)。

您可以使用拖放方法開啟.rc 檔之間[在專案外部](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。

### <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>若要使用拖放方法的檔案間複製資源

1. 開啟這兩個獨立的資源檔案 (如需詳細資訊，請參閱 <<c0> [ 檢視中的.rc 檔，在專案外的資源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md))。 例如，開啟*Source1.rc*並*Source2.rc*。

1. 在第一個.rc 檔中，選取您想要複製的資源。 例如，在*Source1.rc*，選取**IDD_DIALOG1**。

1. 按住**Ctrl**鍵並拖曳至第二個.rc 檔的資源。 例如，拖曳**IDD_DIALOG1**從*Source1.rc*來*Source2.rc*。

   > [!NOTE]
   > 拖曳資源，不需按著**Ctrl**鍵會移動資源，而不是複製它。

### <a name="to-copy-resources-using-copy-and-paste"></a>複製資源使用複製和貼上

1. 開啟這兩個獨立的資源檔案 (如需詳細資訊，請參閱 <<c0> [ 檢視中的.rc 檔，在專案外的資源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md))。 例如， *Source1.rc*並*Source2.rc*。

1. 原始程式檔要複製的資源 (例如*Source1.rc*)，以滑鼠右鍵按一下資源，然後選擇**複製**從捷徑功能表。

1. 以滑鼠右鍵按一下您想要貼上資源所在的資源檔 (例如*Source2.rc*)。 選擇**貼上**從捷徑功能表。

   > [!NOTE]
   > 您無法拖放、 複製、 剪下，或在專案中的資源檔案之間貼上 (**資源檢視**) 和獨立的.rc 檔的檔案 （在文件視窗中開啟）。 您可以在舊版的產品來這麼做。

   > [!NOTE]
   > 若要避免衝突的符號名稱或現有的檔案中的值，Visual c + + 可能會變更已傳送的資源的符號值或符號名稱和值時將它複製到新的檔案。

### <a name="to-change-the-language-or-condition-of-a-resource-while-copying"></a>若要複製時變更其語言或條件的資源

在資源中複製時，您可以變更其語言屬性或條件屬性，或兩者。

- 資源的語言就是識別資源的語言。 所使用的語言[FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea)來協助識別您要尋找的資源。 不過，資源可以有針對每種語言與文字無關的差異 (例如，只適用於日文鍵盤的加速器或點陣圖，只會適用於中文當地語系化組建。）

- 資源的條件是已定義的符號，用來識別使用此特定資源副本時的條件。

語言和資源的條件會顯示在括號中的資源名稱後面**工作區**視窗。 在此範例中，具名資源`IDD_AboutBox`使用`Finnish`做為其語言和其條件是`XX33`。

```cpp
IDD_AboutBox (Finnish - XX33)
```

若要複製現有的資源，並變更其語言或條件：

1. 在.rc 檔中或在[資源檢視](../windows/resource-view-window.md) 視窗中，以滑鼠右鍵按一下您想要複製的資源。

1. 選擇**插入複本**從捷徑功能表。

1. 在 [**插入資源複本**] 對話方塊中：

   - 針對**語言**清單方塊中，選取的語言。

   - 在 **條件**方塊中，輸入條件。

## <a name="to-edit-managed-resource-files"></a>若要編輯 managed 的資源檔

Managed 的資源檔 (.resx) 是 XML 檔案。 當您將受管理的資源檔加入您的專案從**加入新項目** 對話方塊中， **Managed 資源編輯器**預設會開啟。

## <a name="to-import-and-export-resources"></a>匯入和匯出資源

您可以匯入圖形資源 (點陣圖、圖示、游標和工具列)、HTML 檔案，及在 Visual C++ 中使用的自訂資源。 您可以從 Visual C++ 專案匯出相同類型的檔案，分隔可以在開發環境外部使用的檔案。

> [!NOTE]
> 資源類型 (例如加速器、對話方塊和字串資料表) 無法匯入或匯出，因為它們不是獨立的檔案類型。

### <a name="to-import-an-individual-resource-into-your-current-resource-file"></a>將個別的資源匯入目前的資源檔

1. 在[資源檢視](../windows/resource-view-window.md)，以滑鼠右鍵按一下 [] 節點的資源指令碼 (*.rc) 您要將資源新增的檔案。

1. 選取 **匯入**快顯功能表。

1. 找出並選取點陣圖 (.bmp)、圖示 (.ico)、游標 (.cur)、Html 檔案 (.htm)，或是您要匯入的其他檔案的檔案名稱。

1. 選擇 **[確定]** 中選取的檔案中加入資源**資源**檢視。

   > [!NOTE]
   > 無論選取哪一種特定的資源類型，匯入程序都會以相同的方式運作。 會針對該資源類型，將匯入的資源自動加入至正確的節點。

### <a name="to-export-a-bitmap-icon-or-cursor-as-a-separate-file-for-use-outside-of-visual-c"></a>匯出點陣圖、圖示或游標做為個別的檔案 (在 Visual C++ 外部使用)

1. 在 **資源**檢視中，以滑鼠右鍵按一下您想要匯出的資源。

1. 選取 **匯出**快顯功能表。

1. 在 **匯出資源**對話方塊方塊中，接受目前的檔案名稱或輸入新密碼。

1. 瀏覽至您要儲存檔案，並選擇的資料夾**匯出**。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源檔](../windows/resource-files-visual-studio.md)<br/>
[資源編輯器](../windows/resource-editors.md)