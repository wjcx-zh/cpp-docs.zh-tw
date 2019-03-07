---
title: HOW TO：建立資源 （c + +）
ms.date: 02/14/2019
f1_keywords:
- vc.editors.resource
- vc.resvw.add.MFC
- vs.resourceview.F1
- vc.editors.insertresource
- vc.editors.newcustomresource
helpviewer_keywords:
- rc files [C++], creating
- .rc files [C++], creating
- resource script files [C++], creating
- resources [C++], viewing
- rc files [C++], viewing resources
- .rc files [C++], viewing resources
- resource script files [C++], viewing resources
- resource script files [C++], opening in text format
- .rc files [C++], opening in text format
- rc files [C++], opening in text format
- rc files [C++], adding MFC support
- .rc files [C++], adding MFC support
- MFC, adding support to resource scripts files
- resource script files [C++], adding MFC support
- toolbars [C++], resources
- resource toolbars
- resources [C++], creating
- Resource View window
- resources [C++], adding
- Add Resource dialog box [C++]
- Custom Resource Type dialog box [C++]
- language-specific template files [C++]
- resource templates
- rct files [C++]
- templates, resource templates
- resources [C++], templates
- .rct files [C++]
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
ms.openlocfilehash: a18c24685ff0d5f65970a094730d1587abffb601
ms.sourcegitcommit: b4645761ce5acf8c2fc7a662334dd5a471ea976d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/07/2019
ms.locfileid: "57563026"
---
# <a name="how-to-create-resources-c"></a>HOW TO：建立資源 （c + +）

您可以針對專案所建立的資源：

- 使用資源指令碼檔。

   > [!NOTE]
   > 在您新增資源之前，就需要此步驟。

- 將資源新增至您的專案，並使用**資源檢視**。

- 使用資源範本來建立自訂的資源。

## <a name="use-resource-script-files"></a>使用資源指令碼檔案

在您建立並將新的資源新增至您的專案之前，您必須先建立資源指令碼 (.rc) 檔。

> [!NOTE]
> 您只可以加入至現有的專案載入 Visual Studio IDE 的資源指令碼檔。 您無法建立獨立的資源指令碼，在專案中，外部，但可以隨時建立資源範本 (.rct) 檔。

### <a name="to-create-a-resource-script-file"></a>若要建立的資源指令碼檔案

1. 將焦點放在您現有的專案資料夾中**方案總管**，例如*MyProject*。

   > [!NOTE]
   > 請勿混淆方案資料夾內專案資料夾**方案總管 中**。 如果您將焦點放在**解決方案**資料夾中，您不需要相同**加入新項目**選項。

1. 在功能表中，移至**專案** > **加入新項目**。

1. 選取  **Visual c + +** 資料夾，然後選擇**資源檔 (.rc)** 右窗格中。

1. 提供資源指令碼檔案中的名稱**名稱**文字方塊中，然後選取**開啟**。

### <a name="to-open-a-resource-script-file"></a>若要開啟資源指令碼檔

您可以檢視資源指令碼檔案中的資源，而不需要開啟一個專案。 指令碼檔案的視窗中開啟文件相對於**資源檢視**。

> [!NOTE]
> 有些命令才會出現的檔案是開啟的獨立的也就是說在專案外，而不先載入專案。 例如，若要使用**另存新檔**命令，並儲存在不同的格式或檔案名稱的檔案，該檔案必須開啟的獨立。

- 若要開啟的專案以外的資源指令碼檔的功能表中，移至**檔案** > **開啟**，然後選擇**檔案**。 瀏覽至資源指令碼檔，反白顯示檔案，然後選擇**開啟**。

    > [!NOTE]
    > 有時候可能會想要檢視您的專案資源指令碼檔案的內容，而不使用資源編輯器開啟資源時。 例如，您可能想要在資源檔中跨所有對話方塊搜尋字串，而不想個別開啟每個對話方塊。 您可以輕鬆開啟資源檔，以文字格式，檢視它所包含的所有資源，並完成文字編輯器所支援的通用作業。
    >
    > 若要文字格式開啟資源指令碼檔，請使用下拉箭號右邊**開啟**按鈕上一個步驟，然後選擇**開啟**。 選取 **原始程式碼 （文字） 編輯器**進出**開啟為**下拉式清單中，選取**文字**並在中開啟資源**原始程式碼**編輯器。

- 若要開啟多個資源指令碼請遵循上述的每個您要開啟的檔案，比方說，相同的步驟*Source1.rc*並*Source2.rc*。 然後，這兩個.rc 檔案開啟時在個別的文件視窗中，使用** 視窗** 功能表或以滑鼠右鍵按一下其中一個檔案，然後選擇**新增水平索引標籤群組**或**新增垂直索引標籤群組**. Windows 現在會並排顯示，讓您同時檢視。

> [!TIP]
> 您可以開啟資源指令碼檔案中的.rc 檔上按一下滑鼠右鍵**方案總管**，並選取**以開啟**，然後選擇**原始程式碼 （文字） 編輯器**。

當您建置 Windows 使用 Microsoft Foundation Class (MFC) 應用程式[MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)，精靈會產生一組基本的檔案，包括資源指令碼 (.rc) 檔)，包含 MFC 的核心功能。 不過，這些特定 MFC 功能無法使用，當編輯.rc 檔不以 MFC 為基礎的 Windows 應用程式。 這包括程式碼精靈、 功能表提示字串、 清單下拉式方塊控制項和 ActiveX 控制項裝載的內容。

- 若要將 MFC 支援與資源指令碼檔開啟時，在**資源檢視**，反白顯示 [資源] 資料夾 (例如*MFC.rc*)。 然後在[屬性 視窗](/visualstudio/ide/reference/properties-window)，將**MFC 模式**來**True**。

  > [!NOTE]
  > 除了設定**MFC 模式**，.rc 檔必須是 MFC 專案的一部分。 只設定**MFC 模式**要 **，則為 True**在.rc 檔案中的 Win32 專案將不會讓您 MFC 功能。

## <a name="create-resources"></a>建立資源

為新的預設資源，這表示不會根據範本時，資源或範本的模式，您可以建立資源。

使用**資源檢視**視窗，以顯示專案中包含的資源檔。 展開最上層資料夾，例如*Project1.rc*，該檔案中顯示的資源類型。 展開以顯示個別的資源，該類型的每個資源類型。

> [!TIP]
> 若要開啟 **資源檢視**視窗中，移至功能表**檢視** > **資源檢視**或按**Ctrl** + **Shift**+**E**。

您也可以使用在上按一下滑鼠右鍵**資源檢視** 視窗來啟動命令的捷徑功能表，或按兩下標題列來停駐和取消停駐視窗。 以滑鼠右鍵按一下標題列命令，以控制視窗的行為。 如需詳細資訊，請參閱 < [Windows Management](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

**資源檢視**windows 包含**加入資源**對話方塊具有下列屬性將資源新增至 c + + Windows 桌面應用程式專案：

| 屬性 | 描述 |
|---|---|
| **資源類型** | 指定您想要建立的資源的類型。<br/><br/>您可以展開資料指標和對話方塊資源類別來顯示額外的資源，都位於 *...\Microsoft visual Studio\<版本\>\VC\VCResourceTemplates\\< LCID\>\mfc.rct*。 如果您需要加入.rct 檔案，請將它們放在這裡，或指定另一個[include 路徑](../windows/how-to-specify-include-directories-for-resources.md)。 在最上層樹狀結構控制項中顯示的資源是 Visual Studio 所提供的預設資源。 .Rct 檔案中的資源會出現在適當分類底下的第二個層級。 沒有任何預先設定的限制，您可以加入的.rct 檔案數目。<br/><br/> |
| **新增** | 建立資源中選取的類型為基礎**資源類型**方塊，然後在適當的編輯器中開啟資源。<br/><br/>例如，如果您建立對話方塊資源時，就會開啟中的資源[對話方塊編輯器](../windows/dialog-editor.md)。 |
| **Import** | 開啟**匯入**對話方塊，即可瀏覽至您想要匯入目前專案的資源。<br/><br/>您可以匯入點陣圖、 圖示、 游標、 HTML、 音效 (。WAV)，或自訂資源檔案。 |
| **自訂** | 開啟**新的自訂資源**對話方塊來建立自訂的資源。<br/><br/>也包含**資源類型**提供一個文字方塊，讓您輸入的自訂資源類型名稱的屬性。 當您結束時，visual c + + 自動將單字的名稱。 自訂資源只會在中編輯[二進位編輯器](../windows/binary-editor.md)。 |

當您建立新的資源時，Visual c + + 會指派一個唯一的名稱，比方說， `IDD_Dialog1`。 您可以藉由編輯資源屬性相關聯的資源編輯器中或在自訂此資源 ID[屬性 視窗](/visualstudio/ide/reference/properties-window)。

> [!NOTE]
> 未指定資源名稱或保留 Visual Studio 的識別碼。 保留的名稱為`DESIGNINFO`， `HWB`，並`TEXTINCLUDE`，而保留的 ID 是`255`。

### <a name="to-create-a-resource"></a>若要建立資源

- 在 **資源檢視**，選取您的.rc 檔，然後使用**編輯** > **加入資源**，然後選擇 要新增至專案的資源類型。

   > [!TIP]
   > 您也可以以滑鼠右鍵按一下.rc 檔中的**資源檢視**，然後選擇**加入資源**從捷徑功能表。

- 在**方案總管**，以滑鼠右鍵按一下專案資料夾，然後選取**新增** > **加入資源**，然後選擇 要新增至專案的資源類型。

   > [!NOTE]
   > 如果您在專案中還沒有.rc 檔，此步驟會建立一個。 接著，您可以重複此步驟，將特定資源類型加入至新的 .rc 檔。

- 在[類別檢視](/visualstudio/ide/viewing-the-structure-of-code)，以滑鼠右鍵按一下類別，然後選取**新增** > **加入資源**，然後選擇 要新增至專案的資源類型。

- 使用功能表**專案** > **加入資源**。

## <a name="use-resource-templates"></a>使用資源範本

資源範本是自訂的資源，您已將它儲存為.rct 檔案。 資源範本再做為起點來建立資源。 資源範本可節省開發的其他資源或共用功能，例如標準控制項或重複項目中的資源群組的時間。 例如，如果您想要包含公司標誌圖示的 [說明] 按鈕，在許多對話方塊中，建立新對話方塊範本，並自訂 [說明] 按鈕和標誌。

自訂資源範本之後儲存您的變更範本資料夾或在 include 路徑中，指定的位置，以便在新的資源範本會出現在其資源類型底下**加入資源** 對話方塊。 您現在可以使用新的資源範本經常需要。

> [!NOTE]
> 資源編輯器會自動提供唯一的資源識別碼。 您可以修改[資源內容](../windows/changing-the-properties-of-a-resource.md)視。

> [!NOTE]
> 將特定語言的範本檔放在主要範本目錄的子目錄中。 例如，英文版的範本檔案會進入 *...\\< 資源範本目錄\>\1033*。
>
> Visual Studio 中的新.rct 檔案搜尋*\Program Files\Microsoft Visual Studio\<版本\>\VC\VCResourceTemplates*， *\Program Files\Microsoft Visual Studio \<版本 > \VC\VCResourceTemplates\\< LCID\>*  （例如 1033 代表英文的 LCID)，或在任何地方[include 路徑](../windows/how-to-specify-include-directories-for-resources.md)。 如果您想要在另一個位置儲存.rct 檔案，您必須新增至 include 路徑的位置。

### <a name="to-create-and-use-a-resource-template"></a>建立和使用資源範本

1. 在 **方案總管**，以滑鼠右鍵按一下您的專案，然後選取**新增** > **加入新項目**。

1. 在 **範本：** 窗格中，選取**資源範本檔 (.rct)**。

1. 提供新的名稱和位置 *.rct*檔案，然後選擇**開啟**。

   新 *.rct*檔案新增至您的專案，並出現在**方案總管**之下**資源**資料夾。

1. 按兩下 *.rct*在文件視窗中開啟的檔案。 若要新增的資源，以滑鼠右鍵按一下 文件視窗中的檔案，然後選擇**加入資源**。

   您可以自訂您新增的資源，並儲存 *.rct*檔案。

1. 在 **資源檢視**窗格中，以滑鼠右鍵按一下 *.rc*檔案，然後選擇**加入資源**。

1. 選取加號 (**+**) 以展開 [資源] 節點並檢視該資源可用的範本資源旁。

1. 按兩下您想要使用的範本。

   視需要在資源編輯器中，您可以修改新增的資源。

### <a name="to-convert-an-existing-resource-file-to-a-template"></a>若要將現有的資源檔轉換成範本

開啟功能表中的資源指令碼檔案，請移至**檔案** > **儲存\< *filename*> 為**。 指定的位置，然後選擇**確定**。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源檔](../windows/resource-files-visual-studio.md)<br/>
[如何：管理來源](../windows/how-to-copy-resources.md)<br/>
[如何：在編譯時間包含資源](../windows/how-to-include-resources-at-compile-time.md)<br/>