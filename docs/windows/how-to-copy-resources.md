---
title: HOW TO：管理資源 (C++)
ms.date: 02/14/2019
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
ms.openlocfilehash: 6b9499fbd806c04774d12750c70816d0312a4e3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345262"
---
# <a name="how-to-manage-resources-c"></a>HOW TO：管理資源 (C++)

## <a name="copy-and-edit-resources"></a>複製和編輯資源

您可以複製資源從一個檔案到另一個不需要變更它們，或將它複製時變更其語言或條件的資源。

您可以輕鬆地將複製資源從現有的資源或可執行檔目前的資源檔。 若要複製的資源，您開啟這兩個同時包含資源的檔案並將項目從一個檔案拖曳到另一個或複製並貼兩個檔案之間。 這個方法適用於資源指令碼 (.rc) 檔和資源範本 (.rct) 檔，以及為可執行檔 (.exe) 檔案。

> [!NOTE]
> 視覺化C++包含您可以使用自己的應用程式中的範例資源檔案。 如需詳細資訊，請參閱[美工圖案：通用資源](https://github.com/Microsoft/VCSamples)。

您無法拖放、 複製、 剪下，或在專案中的資源檔案之間貼上 (**資源檢視**) 和獨立的.rc 檔在文件視窗中開啟。 您可以在舊版的產品來這麼做。 只能使用已開啟專案外部的.rc 檔之間的拖放方法。

### <a name="to-copy-resources"></a>若要複製資源

1. 開啟兩個獨立資源檔案。 (請參閱[使用資源指令碼檔](how-to-create-a-resource-script-file.md#use-resource-script-files))。 例如，開啟*Source1.rc*並*Source2.rc*。

1. 在第一個.rc 檔，可能是：

   - 使用拖放方法

      1. 選取您想要複製的資源。 例如，在*Source1.rc*，選取**IDD_DIALOG1**。

      1. 按住**Ctrl**鍵並拖曳至第二個.rc 檔的資源。 例如，拖曳**IDD_DIALOG1**從*Source1.rc*來*Source2.rc*。

         > [!TIP]
         > 拖曳資源，不需按著**Ctrl**鍵會移動資源，而不是複製它。

   - 使用複製並貼上的方法

      1. 以滑鼠右鍵按一下 資源與您要複製 (比方說， *Source1.rc*)，然後選擇**複製**。

      1. 以滑鼠右鍵按一下您想要貼上資源所在的資源檔 (例如*Source2.rc*)，然後選擇**貼上**。

> [!NOTE]
> 若要避免衝突的符號名稱或現有的檔案，視覺效果中的值C++可能會變更已傳送的資源的符號值或符號名稱和值時將它複製到新的檔案。

在資源中複製時，您可以變更其語言屬性或條件屬性，或兩者。

- 資源的語言指定所使用的語言[FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea)來協助識別您要尋找的資源。 資源可以有針對每種語言與文字無關的差異，例如，只適用於日文鍵盤的加速器或點陣圖，只會適用於中文當地語系化組建。

- 資源的條件是已定義的符號，用來識別使用此特定資源副本時的條件。

語言和資源的條件會顯示在括號中的資源名稱後面**工作區**視窗。 這裡的具名資源`IDD_AboutBox`使用`Finnish`做為其語言和其條件是`XX33`:

```cpp
IDD_AboutBox (Finnish - XX33)
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>複製現有的資源並變更其語言或條件

在  *.rc*檔案或在[資源檢視](how-to-create-a-resource-script-file.md#create-resources)視窗中，以滑鼠右鍵按一下您想要複製，然後選擇 的資源**插入複本**。 然後設定下列項目：

- 針對**語言**清單方塊中，選取的語言。

- 在 **條件**方塊中，輸入條件。

### <a name="to-edit-resources"></a>若要編輯資源

受管理的資源 (.resx) 檔案是 XML 檔案。 當您將受管理的資源檔加入您的專案從**加入新項目** 對話方塊中， **Managed 資源編輯器**預設會開啟。

## <a name="import-and-export-resources"></a>匯入和匯出資源

您可以匯入圖形資源 (點陣圖、圖示、游標和工具列)、HTML 檔案，及在 Visual C++ 中使用的自訂資源。 您可以從 Visual C++ 專案匯出相同類型的檔案，分隔可以在開發環境外部使用的檔案。

> [!NOTE]
> 無法匯入或匯出，因為它們並非獨立的檔案類型的資源類型，例如加速器、 對話方塊和字串資料表。

### <a name="to-import-a-resource-into-the-resource-script-file"></a>將資源匯入資源指令碼檔

1. 在 [資源檢視](how-to-create-a-resource-script-file.md#create-resources)以滑鼠右鍵按一下您想要加入資源，然後選取資源指令碼 (.rc) 檔的節點**匯入**。

1. 找出並選擇點陣圖 (.bmp)、 圖示 (.ico)、 游標 (.cur)、 html 檔案 (.htm) 或要匯入其他檔案的檔案名稱。

1. 選取 **確定**將資源新增至資源指令碼檔。

> [!NOTE]
> 匯入程序的運作方式相同的無論何種資源類型，您已選取。 匯入的資源會自動加入至該資源類型的正確節點。

### <a name="to-export-a-resource-for-use-outside-of-visual-c"></a>若要匯出視覺效果之外使用的資源C++

1. 在 [資源檢視](how-to-create-a-resource-script-file.md#create-resources)，以滑鼠右鍵按一下您想要匯出，然後選取的資源**匯出**。 您可以接受目前的檔案名稱，或輸入新密碼。

1. 瀏覽至您想要用來儲存檔案，並選取資料夾**匯出**。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源檔](../windows/resource-files-visual-studio.md)<br/>
[如何：建立資源](../windows/how-to-create-a-resource-script-file.md)<br/>
[如何：在編譯時間包含資源](../windows/how-to-include-resources-at-compile-time.md)<br/>