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
ms.openlocfilehash: dbb1d1d4b865380abde189ae6a72a1bfc3755840
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320844"
---
# <a name="how-to-create-resources-c"></a>HOW TO：建立資源 （c + +）

**資源檢視**視窗會顯示在您的專案中包含的資源檔。 展開最上層資料夾 (例如*Project1.rc*) 顯示中的資源類型的檔案，然後展開每個資源類型顯示該類型的個別資源。

> [!TIP]
> 若要開啟 [資源檢視] 視窗，請選取**資源檢視**上**檢視**功能表 (或使用**Ctrl** + **Shift**  +  **E**)。
>
> 您也可以使用在上按一下滑鼠右鍵**資源檢視**以啟動命令的捷徑功能表，或按兩下標題列來停駐或取消停駐視窗的視窗。 以滑鼠右鍵按一下標題列會提供其他命令，可讓您控制視窗的行為。 如需詳細資訊，請參閱 < [Windows Management](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

**資源檢視**windows 包含**加入資源**對話方塊具有下列屬性將資源新增至 c + + Windows 桌面應用程式專案：

|屬性|描述|
|--|----|
|**資源類型**|指定您想要建立的資源種類。<br/><br/>您可以展開資料指標和對話方塊資源類別來顯示其他資源。 這些資源位於 Visual Studio...\Microsoft\<版本\>\VC\VCResourceTemplates\\< LCID\>\mfc.rct。 如果您加入.rct 檔案，請將它們放在此目錄或指定另一個[include 路徑](../windows/how-to-specify-include-directories-for-resources.md)。 如此，那些檔案中的資源將會顯示在適當分類底下的第二層。 沒有任何預先設定的限制，您可以加入的.rct 檔案數目。<br/><br/>樹狀目錄控制項最上層所顯示的資源，是 Visual Studio 所提供的預設資源。|
|**新增**|建立資源中選取的類型為基礎**資源類型**方塊，並在適當的編輯器中開啟資源。 例如，如果您建立對話方塊資源時，它會在中開啟[對話方塊編輯器](../windows/dialog-editor.md)。|
|**Import**|會開啟**匯入**對話方塊中，您可以瀏覽至資源您要匯入至目前的專案。 您可以匯入點陣圖、 圖示、 游標、 HTML、 音效 (。WAV)，或自訂資源檔案。|
|**自訂**|會開啟**新的自訂資源**對話方塊中，您可以在其中建立自訂的資源。 自訂資源只能在二進位編輯器中編輯。|

**加入資源**對話方塊包含**新增自訂資源**具有下列屬性，以 c + + 專案中建立新的自訂資源對話方塊：

|屬性|描述|
|--|----|
|**資源類型**|提供文字方塊中，輸入自訂資源類型的名稱。 Visual c + + 自動將單字的名稱，當您結束**新的自訂資源** 對話方塊。|

> [!NOTE]
> **資源編輯器**或是**資源檢視**在 Express 版中無法使用。

## <a name="resource-scripts"></a>資源指令碼

在您建立並將新的資源新增至您的專案之前，您必須先建立資源指令碼 （.rc 檔）。

> [!NOTE]
> 您只能將資源指令碼 (.rc 檔) 加入已載入 Visual Studio IDE 的現有專案中， 您無法建立獨立的資源指令碼 （專案外部的）。 資源範本 （.rct 檔） 則可以隨時建立。

### <a name="to-create-a-resource-script"></a>若要建立的資源指令碼

1. 將焦點放在您現有的專案資料夾中**方案總管**，例如*MyProject*。

   > [!NOTE]
   > 請勿混淆方案資料夾內專案資料夾**方案總管 中**。 如果您將焦點放在**解決方案**資料夾中，您的選擇中**加入新項目**對話方塊將會不同。

1. 在 [專案] 功能表中，選取 [新增新項目]。

1. 選取  **Visual c + +** 資料夾，然後選擇**資源檔 (.rc)** 右窗格中。

1. 提供資源指令碼中的名稱**名稱**文字方塊中，然後選取**開啟**。

### <a name="to-open-a-resource-script"></a>若要開啟資源指令碼

您可以檢視資源指令碼中的資源，而不需要開啟一個專案。 指令碼檔案會在相對於文件視窗中開啟**資源檢視**視窗。

> [!NOTE]
> （專案） 外的獨立開啟的檔案時，才可以使用一些命令。 開啟檔案的獨立表示開啟而不先載入專案。
>
> 例如，若要將檔案儲存在不同的格式，或做為不同的檔案名稱 (作為**另存新檔**命令不適用於專案內的檔案)。 如果您開啟專案先使用**檔案** > **開啟** > **專案**，這些命令無法使用。

#### <a name="to-open-a-resource-script-outside-of-a-project"></a>若要開啟專案外的資源指令碼

1. 從**檔案**功能表上，選取**開放**，然後選擇**檔案**。

1. 瀏覽至資源指令碼檔，反白顯示檔案，然後選擇**開啟**。

#### <a name="to-open-multiple-resource-scripts-outside-of-a-project"></a>若要開啟專案外的多個資源指令碼

1. 開啟兩個獨立資源檔案。 例如，開啟*Source1.rc*並*Source2.rc*。

1. 從**檔案**功能表上，選擇**開放**，然後選取**檔案**。

1. 巡覽至您想要開啟的第一個資源指令碼檔案 (*Source1.rc*)，反白顯示檔案，然後選擇**開啟**。

1. 重複上述步驟來開啟第二個.rc 檔 (*Source2.rc*)。

   這兩個.rc 檔現在會開啟在個別的文件視窗中。

1. 使用** 視窗**功能表 （或滑鼠右鍵按一下其中一個.rc 檔），然後選擇**新增水平索引標籤群組**或是**新增垂直索引標籤群組**。

   Windows 現在會並排顯示，讓您同時檢視。

有時候您會想要檢視專案資源指令碼 (.rc) 檔內容，而不想開啟其特定資源編輯器內的資源 (例如對話方塊)。 例如，您可能想要在資源檔中跨所有對話方塊搜尋字串，而不想個別開啟每個對話方塊。

您可以輕鬆開啟資源檔，以文字格式，檢視它所包含的所有資源，並完成文字編輯器所支援的通用作業。

> [!NOTE]
> 資源編輯器不會直接讀取.rc 或`resource.h`檔案。 資源編譯器會將它們編譯成 .aps 檔，以供資源編輯器使用。 此檔案是一個編譯步驟，只會儲存符號資料。 如同正常的編譯程序一般，編譯程序期間會捨棄非符號的資訊 (例如註解)。 每當.aps 檔未與.rc 檔取得同步的都會重新產生.rc 檔案 (例如，當您儲存時，資源編輯器會覆寫.rc 檔和`resource.h`檔案)。 資源本身的任何變更繼續合併在.rc 檔，但一旦.rc 檔被覆寫，註解都會遺失。 如需如何保留註解的資訊，請參閱[在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)。

### <a name="to-open-a-resource-script-file-in-text-format"></a>若要以文字格式開啟資源指令碼檔

1. 從**檔案**功能表中，選取**開放**，然後選擇**檔案**。

1. 在 **開啟檔案**對話方塊方塊中，瀏覽至您想要以文字格式檢視資源指令碼檔。

1. 反白顯示檔案，然後選取上的下拉箭號**開啟**按鈕 （右邊的按鈕）。

1. 選擇**開啟**從下拉功能表並選取**原始程式碼 （文字） 編輯器**。

1. 從**開啟為**下拉式清單中，選取**文字**。

   資源會在中開啟**原始程式碼**編輯器。

> [!TIP]
> 是以滑鼠右鍵按一下.rc 檔中的的捷徑**方案總管**，選擇**開啟方式...** ，然後選取**原始程式碼 （文字） 編輯器**。

## <a name="resources"></a>資源

您可以在為新的預設資源 （不以範本為基礎的資源），或為模仿範本資源建立資源。

當您建立新的資源時，Visual c + + 會指派一個唯一的名稱，比方說， `IDD_Dialog1`。 您可以在相關聯的資源編輯器中或在 [ [屬性視窗](/visualstudio/ide/reference/properties-window)] 中編輯資源的屬性，以自訂此資源 ID。

> [!NOTE]
> 未指定資源名稱或保留 Visual Studio 的識別碼。 保留的名稱為 DESIGNINFO、 HWB 和 TEXTINCLUDE，而保留的 ID 為 255。

### <a name="to-create-a-resource"></a>若要建立資源

您可以建立新的資源，使用下列其中一項：

- 在 **資源檢視**，選取您的.rc 檔，然後使用**編輯** > **加入資源**，然後選擇 要新增至專案的資源類型。

   > [!TIP]
   > 您也可以以滑鼠右鍵按一下.rc 檔中的**資源檢視**，然後選擇**加入資源**從捷徑功能表。

- 在**方案總管**，以滑鼠右鍵按一下專案資料夾，然後選取**新增** > **加入資源**，然後選擇 要新增至專案的資源類型。

   > [!NOTE]
   > 如果您在專案中還沒有.rc 檔，此步驟會建立一個。 接著，您可以重複此步驟，將特定資源類型加入至新的 .rc 檔。

- 在[類別檢視](/visualstudio/ide/viewing-the-structure-of-code)，以滑鼠右鍵按一下類別，然後選取**新增** > **加入資源**，然後選擇 要新增至專案的資源類型。

- 在 **專案**功能表上，選取**加入資源**。

### <a name="support-for-mfc"></a>MFC 支援

一般來說，如果 Windows 使用 Microsoft Foundation Class (MFC) 應用程式建置[MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)，精靈會產生一組基本的檔案 （包括資源指令碼 (.rc) 檔），其中包含核心功能MFC。 不過，編輯.rc 檔案，不以 MFC 為基礎的 Windows 應用程式時，無法使用下列特定 MFC 的功能：MFC 程式碼精靈，功能表提示字串，會列出下拉式方塊控制項和 ActiveX 控制項裝載的內容。

#### <a name="to-add-mfc-support-to-a-resource-script-file"></a>將 MFC 支援新增至資源指令碼檔

1. 開啟資源指令碼檔案。

1. 在 **資源檢視**，反白顯示 資源 資料夾 (例如*MFC.rc*)。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，將**MFC 模式**屬性設 **，則為 True**。

   > [!NOTE]
   > 除了設定這個屬性，在.rc 檔必須是 MFC 專案的一部分。 比方說，就是直接設定**MFC 模式**要 **，則為 True**在.rc 檔案中的 Win32 專案將不會讓您 MFC 功能。

## <a name="resource-templates"></a>資源範本

資源範本是自訂的資源，您已將它儲存為.rct 檔案。 資源範本再做為起點來建立資源。 資源範本可節省開發的其他資源或共用功能，例如標準控制項或重複項目中的資源群組的時間。 例如，如果您想要包含公司標誌圖示的 [說明] 按鈕，在許多對話方塊中，建立新對話方塊範本，並自訂 [說明] 按鈕和標誌。

自訂資源範本之後，請在範本資料夾 （或 include 路徑中指定的位置） 中儲存您的變更，讓新的資源範本會出現在其資源類型底下**加入資源** 對話方塊。 您現在可以使用新的資源範本經常需要。

> [!NOTE]
> 資源編輯器會自動提供唯一的資源識別碼。 您可以修改[資源內容](../windows/changing-the-properties-of-a-resource.md)視。

> [!NOTE]
> 將特定語言的範本檔放在主要範本目錄的子目錄中。 例如，將放在英文版的範本檔案...\\< 資源範本目錄\>\1033。 Visual Studio 中的新 RCT 檔案 \Program Files\Microsoft Visual Studio 會搜尋\<版本\>\VC\VCResourceTemplates，在 Visual Studio \Program Files\Microsoft\<版本 > \VC\VCResourceTemplates\\< LCID\> （例如 1033 代表英文)*或是*上的任何位置[include 路徑](../windows/how-to-specify-include-directories-for-resources.md)。 如果您想要將 RCT 檔案儲存在另一個位置，例如我的文件，您需要將此資料夾新增至 include 路徑，讓 Visual Studio 可以找到您的 RCT 檔案。

### <a name="to-create-a-resource-template"></a>若要建立的資源範本

1. 在 [**方案總管] 中**，以滑鼠右鍵按一下您的專案。

1. 從捷徑功能表，選取**新增** > **加入新項目**。

1. 在 **範本：** 窗格中，選取**資源範本檔 (.rct)**。

1. 提供的名稱和您的新.rct 檔案的位置，然後選擇**開啟**。

   新的.rct 檔案新增至您的專案，並出現在**方案總管**下方**資源**資料夾。

1. 按兩下.rct 檔案以在文件視窗中開啟它。 若要新增的資源，以滑鼠右鍵按一下 文件視窗中的檔案，然後選擇**加入資源**。

   您可以自訂這些資源，並儲存.rct 檔案。

### <a name="to-create-a-new-resource-from-a-template"></a>從範本建立新資源

1. 在 **資源檢視**窗格中，以滑鼠右鍵按一下.rc 檔，然後選擇**加入資源**從捷徑功能表。

1. 選取加號 (**+**) 旁邊要展開資源節點，然後檢視該資源可用的所有範本的資源。

1. 按兩下您想要使用的範本。

1. 在資源編輯器中視需要修改所加入的資源。

### <a name="to-convert-an-existing-resource-file-to-a-template"></a>若要將現有的資源檔轉換成範本

1. 將.rc 檔案開啟為獨立的檔案。

1. 在 **檔案**功能表上，選取**儲存\<*檔名*> 為**。

1. 指定的位置，然後選擇**確定**。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源檔](../windows/resource-files-visual-studio.md)<br/>
[管理資源](../windows/how-to-copy-resources.md)<br/>
[在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)<br/>