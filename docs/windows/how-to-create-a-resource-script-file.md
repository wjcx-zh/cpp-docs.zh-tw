---
title: 作法：建立資源（C++）
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
ms.openlocfilehash: c997c7a1b2d7fb3a852a42fa78faf2be6074705e
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444972"
---
# <a name="how-to-create-resources-c"></a>作法：建立資源（C++）

您可以藉由下列方式建立專案的資源：

- 使用資源腳本檔案。

   > [!NOTE]
   > 您必須先執行此步驟，才能新增資源。

- 將資源新增至您的專案，並使用**資源檢視**。

- 使用資源範本來建立自訂資源。

## <a name="use-resource-script-files"></a>使用資源腳本檔案

在您建立新資源並將其加入至專案之前，您必須先建立資源腳本（.rc）檔案。

> [!NOTE]
> 您只能將資源腳本檔案加入至載入 Visual Studio IDE 的現有專案。 您無法在專案外建立獨立的資源腳本，不過可以隨時建立資源範本（.rct）檔案。

### <a name="to-create-a-resource-script-file"></a>若要建立資源腳本檔

1. 將焦點放在**方案總管**的現有專案資料夾中，例如*MyProject*。

   > [!NOTE]
   > 請不要將專案資料夾與**方案總管**中的 [方案] 資料夾混淆。 如果您將焦點放在**方案**資料夾，則不會有相同的 [**加入新專案**] 選項。

1. 在功能表中，移至 [**專案**] > [**加入新專案**]。

1. 選取 [**視覺C++效果**] 資料夾，然後選擇右窗格中的 [**資源檔（.rc）** ]。

1. 在 [**名稱**] 文字方塊中提供資源腳本檔的名稱，然後選取 [**開啟**]。

### <a name="to-open-a-resource-script-file"></a>若要開啟資源腳本檔案

您可以在資源腳本檔案中查看資源，而不需要開啟專案。 腳本檔案會在文件視窗中開啟，而不是**資源檢視**。

> [!NOTE]
> 某些命令只有在檔案獨立開啟時才可使用，這表示不需要先載入專案，就會在專案之外。 例如，若要使用 [**另存**新檔] 命令，並以不同的格式或檔案名儲存檔案，則必須單獨開啟該檔案。

- 若要開啟專案外的資源腳本檔案，請在功能表中，移至 檔案 ** > ** **開啟**，**然後選擇** 檔案。 流覽至資源腳本檔，反白顯示檔案，然後選擇 [**開啟**]。

    > [!NOTE]
    > 有時候，您可能會想要查看專案的資源腳本檔案內容，而不需使用資源編輯器來開啟資源。 例如，您可能想要在資源檔中跨所有對話方塊搜尋字串，而不想個別開啟每個對話方塊。 您可以輕鬆地以文字格式開啟資源檔，以查看它所包含的所有資源，並完成文字編輯器支援的全域作業。
    >
    > 若要以文字格式開啟資源腳本檔，請使用上一個步驟中 [**開啟**] 按鈕右邊的下拉箭號，然後選擇 [**開啟方式**]。 選取 [**原始程式碼（文字）編輯器**]，然後從 [**開啟為**] 下拉式清單中選取 [**文字**]，然後在**原始程式碼**編輯器中開啟資源。

- 若要開啟多個資源腳本，請針對您要開啟的每個檔案遵循相同的步驟，例如*source1.rc .rc*和*Source2。* 然後，當兩個 .rc 檔都在不同的文件視窗中開啟時，請使用 [**視窗]** 功能表，或以滑鼠右鍵按一下其中一個檔案，然後選擇 [**新增水準**索引標籤群組] 或 [新增垂直索引標籤**群組]** 。 視窗現在會進行磚，讓您可以同時進行查看。

> [!TIP]
> 以滑鼠右鍵按一下**方案總管**中的 .rc 檔，選取 [**開啟方式**]，然後選擇 [**原始程式碼（文字）編輯器**]，即可開啟資源腳本檔案。

當您使用[MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)建立適用于 Windows 的 Microsoft Foundation CLASS （mfc）應用程式時，此 wizard 會產生一組基本的檔案（包括資源腳本（.rc）檔），其中包含 MFC 的核心功能。 不過，編輯不是以 MFC 為基礎的 Windows 應用程式的 .rc 檔時，無法使用這些 MFC 特有的功能。 這包括程式碼嚮導、功能表提示字串、下拉式方塊控制項的清單內容，以及 ActiveX 控制項裝載。

- 若要加入 MFC 支援，並開啟資源腳本檔案，請在 **資源檢視**中，反白顯示 資源 資料夾（例如， *MFC .rc*）。 然後在[屬性視窗](/visualstudio/ide/reference/properties-window)中，將 [ **MFC 模式]** 設定為 [ **True**]。

  > [!NOTE]
  > 除了設定**Mfc 模式**，.rc 檔案也必須是 mfc 專案的一部分。 只有在 Win32 專案的 .rc 檔上將 [ **Mfc 模式]** 設定為 [ **True** ]，才不會提供 mfc 功能。

## <a name="create-resources"></a>建立資源

您可以將資源建立為新的預設資源，表示不是以範本為基礎的資源，或做為範本後面的資源。

使用 [**資源檢視**] 視窗，即可顯示專案中包含的資源檔。 展開頂端資料夾（例如， *Project1*）會顯示該檔案內的資源類型。 展開每個資源類型，以顯示該類型的個別資源。

> [!TIP]
> 若要開啟 [**資源檢視**] 視窗，請移至功能表**視圖** > **其他視窗** > **資源檢視**或按**Ctrl**+**Shift**+**E**。

您也可以使用滑鼠右鍵按一下 [**資源檢視**] 視窗，啟動命令的快捷方式功能表，或按兩下標題列來停駐和取消停駐視窗。 以滑鼠右鍵按一下控制視窗行為之命令的標題列。 如需詳細資訊，請參閱[Windows Management](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

**資源檢視**windows 包含 [**加入資源**] 對話方塊，其中包含下列屬性，可將資源新增C++至 windows 桌面應用程式專案：

| 屬性 | 描述 |
|---|---|
| **資源類型** | 指定您想要建立的資源類型。<br/><br/>您可以展開資料指標和對話方塊資源類別，以顯示位於. 中的其他資源。 *\Microsoft Visual Studio \<版本\>\VC\VCResourceTemplates\\< LCID\>\mfc.rct*。 如果您需要新增 .rct 檔案，請將它們放在此處，或指定另一個[include 路徑](../windows/how-to-specify-include-directories-for-resources.md)。 樹狀目錄控制項最上層顯示的資源是 Visual Studio 所提供的預設資源。 .Rct 檔案中的資源會出現在適當類別下的第二個層級。 您可以新增的 .rct 檔案數目沒有預設限制。<br/><br/> |
| **新增** | 根據在 [**資源類型**] 方塊中選取的類型來建立資源，並在適當的編輯器中開啟資源。<br/><br/>例如，如果您建立對話方塊資源，它會在[對話方塊編輯器](../windows/dialog-editor.md)中開啟資源。 |
| **Import** | 開啟 [匯**入**] 對話方塊，以流覽至您要匯入至目前專案的資源。<br/><br/>您可以匯入點陣圖、圖示、游標、HTML、音效（。WAV）或自訂資源檔。 |
| **自訂** | 開啟 [**新增自訂資源**] 對話方塊，以建立自訂資源。<br/><br/>也包含**資源類型**屬性，可提供文字方塊讓您輸入自訂資源類型的名稱。 當C++您結束時，視覺效果會自動將名稱設為大寫。 自訂資源只會在[二進位編輯器](../windows/binary-editor.md)中編輯。 |

當您建立新的資源時， C++視覺效果會為其指派唯一的名稱，例如 `IDD_Dialog1`。 您可以在相關聯的資源編輯器或[屬性視窗](/visualstudio/ide/reference/properties-window)中編輯資源屬性，以自訂此資源識別碼。

> [!NOTE]
> 請勿指定 Visual Studio 保留的資源名稱或識別碼。 保留的名稱會 `DESIGNINFO`、`HWB`和 `TEXTINCLUDE`，而保留的識別碼會 `255`。

### <a name="to-create-a-resource"></a>若要建立資源

- 在**資源檢視**中，選取您的 .rc 檔，然後使用 **編輯** > **新增資源**，然後選擇要新增至專案的資源類型。

   > [!TIP]
   > 您也可以在**資源檢視**中，以滑鼠右鍵按一下 .rc 檔，然後從快捷方式功能表選擇 [**加入資源**]。

- 在**方案總管**中，以滑鼠右鍵按一下專案資料夾，選取 **新增** > **新增資源**，然後選擇要加入至專案的資源類型。

   > [!NOTE]
   > 如果您的專案中還沒有 .rc 檔案，此步驟會建立一個。 接著，您可以重複此步驟，將特定資源類型加入至新的 .rc 檔。

- 在[類別檢視](/visualstudio/ide/viewing-the-structure-of-code)中，以滑鼠右鍵按一下類別，選取 [**新增** > **新增資源**]，然後選擇要新增至專案的資源類型。

- 使用功能表**專案** > **新增資源**。

## <a name="use-resource-templates"></a>使用資源範本

資源範本是您已儲存為 .rct 檔案的自訂資源。 接著，資源範本會作為建立資源的起點。 資源範本可節省開發其他資源的時間，或是共用功能的資源群組，例如標準控制項或重複的元素。 例如，如果您想要在數個對話方塊中包含公司標誌圖示的 [說明] 按鈕，請建立新的對話方塊範本，並使用 [說明] 按鈕和標誌進行自訂。

自訂資源範本之後，請將您的變更儲存在範本資料夾或 include 路徑中指定的位置，讓新的資源範本出現在 [**新增資源**] 對話方塊的資源類型下。 您現在可以視需要經常使用新的資源範本。

> [!NOTE]
> 資源編輯器會自動提供唯一的資源識別碼。 您可以視需要修改[資源屬性](../windows/changing-the-properties-of-a-resource.md)。

> [!NOTE]
> 將語言特定的範本檔案放在主要範本目錄的子目錄中。 例如，僅限英文的範本檔案會移至 *\\< 資源範本目錄\>\ 1033*。
>
> Visual Studio 搜尋 \Program Files\Microsoft 中的新 .rct 檔案*Visual Studio \<版本\>\VC\VCResourceTemplates*、 *\Program Files\Microsoft Visual Studio \<版本 > \VC\VCRESOURCETEMPLATES\\< LCID\>* （例如1033的 lcid 為英文），或[包含路徑](../windows/how-to-specify-include-directories-for-resources.md)的任何位置。 如果您想要將 .rct 檔案儲存在另一個位置，您必須將位置加入至 include 路徑。

### <a name="to-create-and-use-a-resource-template"></a>建立和使用資源範本

1. 在**方案總管**中，以滑鼠右鍵按一下您的專案，**然後選取 新增** > **加入新專案**。

1. 在 [**範本：** ] 窗格中，選取 [**資源範本檔案（.rct）** ]。

1. 提供新 *.rct*檔案的名稱和位置，然後選擇 [**開啟**]。

   新的 *.rct*檔案會加入至您的專案，並出現在**方案總管**[**資源**] 資料夾下。

1. 按兩下 *.rct*檔案，在文件視窗中開啟它。 若要新增資源，請在文件視窗中的檔案上按一下滑鼠右鍵，然後選擇 [**新增資源**]。

   您可以自訂已加入的資源，並儲存 *.rct*檔案。

1. 在 [**資源檢視**] 窗格中，以滑鼠右鍵按一下 *.rc*檔，然後選擇 [**新增資源**]。

1. 選取資源旁邊的加號（ **+** ），以展開資源節點，並查看該資源可用的範本。

1. 按兩下您想要使用的範本。

   您可以視需要在其資源編輯器中修改新增的資源。

### <a name="to-convert-an-existing-resource-file-to-a-template"></a>若要將現有的資源檔轉換成範本

當資源腳本檔案開啟時，請在功能表中，移至 [檔案 **] > ** **將 \<*filename*> 儲存為**。 指定位置，然後選擇 **[確定]** 。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源檔](../windows/resource-files-visual-studio.md)<br/>
[如何：管理來源](../windows/how-to-copy-resources.md)<br/>
[如何：在編譯時間包含資源](../windows/how-to-include-resources-at-compile-time.md)<br/>