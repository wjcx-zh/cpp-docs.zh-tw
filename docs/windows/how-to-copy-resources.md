---
title: 如何：管理資源（C++）
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
ms.openlocfilehash: 718de310bc4fb0cb0072065bc4e7b7adadb182aa
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890924"
---
# <a name="how-to-manage-resources-c"></a>如何：管理資源（C++）

## <a name="copy-and-edit-resources"></a>複製和編輯資源

您可以將資源從某個檔案複製到另一個檔案，而不需要變更它們，或在複製資源時變更其語言或條件。

您可以輕鬆地將資源從現有的資源或可執行檔案複製到目前的資源檔。 若要複製資源，您可以同時開啟包含資源的兩個檔案，並將專案從某個檔案拖曳到另一個檔案，或在兩個檔案之間複製並貼上。 這個方法適用于資源腳本（.rc）檔案和資源範本（.rct）檔案，以及做為可執行檔（.exe）。

> [!NOTE]
> 視覺C++效果包含您可以在自己的應用程式中使用的範例資源檔。 如需詳細資訊，請參閱美工圖案[：一般資源](https://github.com/Microsoft/VCSamples)。

您無法在專案（**資源檢視**）中的資源檔和在文件視窗中開啟的獨立 .rc 檔案之間拖放、複製、剪下或貼上。 您可以在舊版產品中執行此動作。 請只在專案外部開啟的 .rc 檔案之間使用拖放方法。

### <a name="to-copy-resources"></a>複製資源

1. 開啟兩個獨立資源檔案。 （請參閱[使用資源腳本](how-to-create-a-resource-script-file.md#use-resource-script-files)檔案）。 例如，開啟*source1.rc*和*Source2*。

1. 在第一個 .rc 檔中，可能是：

   - 使用拖放方法

      1. 選取您想要複製的資源。 例如，在*source1.rc*中，選取 [ **IDD_DIALOG1**]。

      1. 按住**Ctrl**鍵，然後將資源拖曳至第二個 .rc 檔。 例如，將**IDD_DIALOG1**從*Source1.rc*拖曳至*Source2*。

         > [!TIP]
         > 拖曳資源而不按住**Ctrl**鍵，就會移動資源，而不是複製它。

   - 使用複製並貼上方法

      1. 以滑鼠右鍵按一下您要複製的資源（例如， *source1.rc*），然後選擇 [**複製**]。

      1. 以滑鼠右鍵按一下您想要貼上資源的資源檔（例如， *Source2*），然後選擇 [**貼**上]。

> [!NOTE]
> 若要避免與現有檔案中的符號名稱或值衝突， C++視覺效果可能會在您將傳送的資源的符號值或符號名稱和值複製到新檔案時，加以變更。

在資源中複製時，您可以變更其語言屬性或條件屬性，或兩者。

- 資源的語言會指定[FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea)所使用的語言，以協助識別您所尋找的資源。 資源可能會有與文字無關之每種語言的差異，例如，只能在日文鍵盤或點陣圖（僅適用于中文當地語系化的組建）上的快速鍵。

- 資源的條件是已定義的符號，用來識別使用此特定資源副本時的條件。

資源的語言和條件會顯示在 [**工作區**] 視窗中的資源名稱後面的括弧中。 在這裡，名為 `IDD_AboutBox` 的資源使用 `Finnish` 作為其語言，且其條件為 `XX33`：

```cpp
IDD_AboutBox (Finnish - XX33)
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>複製現有的資源並變更其語言或條件

在 *.rc*檔案或 [[資源檢視](how-to-create-a-resource-script-file.md#create-resources)] 視窗中，以滑鼠右鍵按一下您要複製的資源，然後選擇 [**插入複本**]。 然後設定下列各項：

- 針對 [**語言**] 清單方塊，選取語言。

- 在 [**條件**] 方塊中，輸入條件。

### <a name="to-edit-resources"></a>編輯資源

受控資源（.resx）檔案是 XML 檔案。 當您從 [**加入新專案**] 對話方塊將 managed 資源檔加入至專案時，預設會開啟 [ **managed 資源編輯器**]。

## <a name="import-and-export-resources"></a>匯入和匯出資源

您可以匯入圖形資源 (點陣圖、圖示、游標和工具列)、HTML 檔案，及在 Visual C++ 中使用的自訂資源。 您可以從 Visual Studio C++專案匯出相同類型的檔案，以分隔可在開發環境之外使用的檔案。

> [!NOTE]
> 無法匯入或匯出資源類型（例如快速鍵、對話方塊和字串資料表），因為它們不是獨立的檔案類型。

### <a name="to-import-a-resource-into-the-resource-script-file"></a>若要將資源匯入資源腳本檔案

1. 在 [資源檢視](how-to-create-a-resource-script-file.md#create-resources)以滑鼠右鍵按一下您要新增資源的資源腳本（.rc）檔案的節點，然後選取 匯**入**。

1. 找出並選擇點陣圖（.bmp）、圖示（.ico）、游標（中）、html 檔案（.htm）或其他要匯入之檔案的檔案名。

1. 選取 **[確定]** ，將資源加入至資源腳本檔案。

> [!NOTE]
> 無論您選取哪一種資源類型，匯入程式的運作方式都相同。 匯入的資源會自動新增至該資源類型的正確節點。

### <a name="to-export-a-resource-for-use-outside-of-visual-c"></a>匯出資源以在視覺效果之外使用C++

1. 在[資源檢視](how-to-create-a-resource-script-file.md#create-resources)中，以滑鼠右鍵按一下您要匯出的資源，然後選取 [**匯出**]。 您可以接受目前的檔案名，或輸入新的名稱。

1. 流覽至您要儲存檔案的資料夾，然後選取 [**匯出**]。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源檔](../windows/resource-files-visual-studio.md)<br/>
[如何：建立資源](../windows/how-to-create-a-resource-script-file.md)<br/>
[如何：在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)<br/>