---
title: 如何：建立 (c + +) 的資源
ms.date: 02/14/2019
f1_keywords:
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
ms.openlocfilehash: 88618a5b1184ce9774a58f575a3fbff2d5e63ba4
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504429"
---
# <a name="how-to-create-resources-c"></a>如何：建立 (c + +) 的資源

您可以透過下列方式，為您的專案建立資源：

- 使用資源腳本檔案。

   > [!NOTE]
   > 在您新增資源之前，必須執行此步驟。

- 將資源新增至您的專案，並使用 **資源檢視**。

- 使用資源範本來建立自訂資源。

## <a name="use-resource-script-files"></a>使用資源指令檔

在您建立新資源並將其新增至專案之前，您必須先建立 ( .rc) 檔案的資源腳本。

> [!NOTE]
> 您只能將資源腳本檔案新增至載入 Visual Studio IDE 中的現有專案。 您無法在專案之外建立獨立的資源腳本，但是可以隨時建立資源範本 ( .rct) 檔案。

### <a name="to-create-a-resource-script-file"></a>建立資源腳本檔

1. 將焦點放在 **方案總管**中的現有專案資料夾（例如 *MyProject*）。

   > [!NOTE]
   > 請勿混淆專案資料夾與 **方案總管**中的方案資料夾。 如果您將焦點放在 **方案** 資料夾中，則不會有相同的 [ **加入新專案** ] 選項。

1. 在功能表中，移至**Project**的 [  >  **加入新專案**]。

1. 選取 **Visual C++** 資料夾，然後選擇右窗格中的 [ **資源檔 ( .rc) ** 。

1. 在 [ **名稱** ] 文字方塊中提供資源指令檔的名稱，然後選取 [ **開啟**]。

### <a name="to-open-a-resource-script-file"></a>開啟資源腳本檔

您可以在資源腳本檔案中查看資源，而不會開啟專案。 腳本檔案會在文件視窗中開啟，而不是在 **資源檢視**中開啟。

> [!NOTE]
> 某些命令只有在檔案獨立開啟時才可使用，這表示在不先載入專案的專案之外。 例如，若要使用 [ **另存** 新檔] 命令，並以不同的格式或檔案名儲存檔案，則必須單獨開啟該檔案。

- 若要在專案外開啟資源腳本檔，請在功能表中，**移至 [**  >  **開啟**檔案]， **File**然後選擇 [檔案]。 流覽至資源腳本檔、反白顯示檔案，然後選擇 [ **開啟**]。

    > [!NOTE]
    > 有時您可能會想要在不使用資源編輯器開啟資源的情況下，查看專案資源腳本檔案的內容。 例如，您可能想要在資源檔中跨所有對話方塊搜尋字串，而不想個別開啟每個對話方塊。 您可以輕鬆地以文字格式開啟資源檔，以查看其包含的所有資源，並完成文字編輯器所支援的全域作業。
    >
    > 若要以文字格式開啟資源腳本檔，請使用上述步驟中 [ **開啟** ] 按鈕右邊的下拉箭號，然後選擇 [ **開啟方式**]。 選取 [ **原始程式碼] (文字) 編輯器** ，然後從 [ **開啟為** ] 下拉式清單中，選取 [ **文字** ]，然後在 **原始程式碼** 編輯器中開啟資源。

- 若要開啟多個資源腳本，請針對您想要開啟的每個檔案遵循上述相同步驟，例如 *source1.rc .rc* 和 *>source2 .rc*。 然後，當兩個 .rc 檔都在個別的文件視窗中開啟時，請使用 [ **視窗]** 功能表或以滑鼠右鍵按一下其中一個檔案，然後選擇 [新增水準索引標籤 **群組]** 或 [新增垂直索引標籤 **群組]**。 現在會將視窗並排顯示，讓您可以同時進行查看。

> [!TIP]
> 您可以開啟資源腳本檔案，方法是以滑鼠右鍵按一下 **方案總管**中的 .rc 檔，選取 [ **開啟檔案** ]，然後在 [ **) 編輯器] (文字**中選擇 [原始程式碼]。

當您使用 [mfc 應用程式精靈](../mfc/reference/mfc-application-wizard.md)建立 MFC 的 mfc) 應用程式 (mfc 時，wizard 會產生一組基本的檔案，包括資源腳本 ( .rc) 檔案) ，其中包含 MFC 的核心功能。 不過，針對不是以 MFC 為基礎的 Windows 應用程式編輯 .rc 檔時，無法使用這些 MFC 特有的功能。 這包括程式碼的嚮導、功能表提示字串、下拉式方塊控制項的清單內容，以及 ActiveX 控制項裝載。

- 若要加入 MFC 支援，並開啟資源腳本檔，請在 **資源檢視**中，反白顯示 [資源] 資料夾 (例如，[ *mfc .rc*) 。 然後，在 [屬性視窗](/visualstudio/ide/reference/properties-window)中，將 [ **MFC 模式]** 設定為 [ **True**]。

  > [!NOTE]
  > 除了設定 **Mfc 模式**之外，.rc 檔也必須是 mfc 專案的一部分。 只有在 Win32 專案的 .rc 檔上將 [ **Mfc 模式]** 設定為 [ **True** ] 時，才會提供 mfc 功能。

## <a name="create-resources"></a>建立資源

您可以將資源建立為新的預設資源，這表示不是以範本為基礎的資源，或作為範本之後的資源。

使用 **資源檢視** 視窗顯示專案中包含的資源檔。 展開最上層資料夾（例如， *Project1*）會顯示該檔案內的資源類型。 展開每個資源類型，以顯示該類型的個別資源。

> [!TIP]
> 若要開啟**資源檢視**視窗，請移至 [功能表**視圖**  >  **其他視窗**  >  **資源檢視**或按**Ctrl** + **Shift** + **E**。

您也可以使用滑鼠右鍵按一下 **資源檢視** 視窗來啟動命令的快捷方式功能表，或按兩下標題列來停駐和取消停駐視窗。 以滑鼠右鍵按一下控制視窗行為之命令的標題列。 如需詳細資訊，請參閱 [Windows 管理](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

**資源檢視**視窗包含 [**新增資源**] 對話方塊，其中包含下列屬性，可將資源新增至 c + + windows 桌面應用程式專案：

| 屬性 | 描述 |
|---|---|
| **資源類型** | 指定您想要建立的資源類型。<br/><br/>您可以展開資料指標和對話方塊資源類別，以顯示位於中的其他資源 *。\Microsoft Visual Studio \<version\> \VC\VCResourceTemplates \\<LCID \> \mfc.rct*。 如果您需要加入 .rct 檔案，請將它們放在這裡或指定另一個 [include 路徑](./how-to-include-resources-at-compile-time.md)。 樹狀目錄控制項中最上層顯示的資源是 Visual Studio 所提供的預設資源。 .Rct 檔案中的資源會出現在適當類別下的第二個層級。 您可以新增的 .rct 檔案數目沒有預設限制。<br/><br/> |
| **新增** | 根據 [ **資源類型** ] 方塊中所選取的類型來建立資源，並在適當的編輯器中開啟資源。<br/><br/>例如，如果您建立對話方塊資源，它會在 [對話方塊編輯器](../windows/dialog-editor.md)中開啟資源。 |
| **匯入** | 開啟 [匯 **入** ] 對話方塊，以流覽至您想要匯入至目前專案的資源。<br/><br/>您可以匯入點陣圖、圖示、游標、HTML ( 的音效。WAV) 或自訂資源檔。 |
| **Custom** | 開啟 [ **新增自訂資源** ] 對話方塊，以建立自訂資源。<br/><br/>也包含 [ **資源類型** ] 屬性，可提供文字方塊讓您輸入自訂資源類型的名稱。 當您結束時，Visual C++ 會自動將名稱設為大寫。 自訂資源只會在 [二進位編輯器](../windows/binary-editor.md)中編輯。 |

當您建立新的資源時，Visual C++ 會指派唯一的名稱給它，例如 `IDD_Dialog1` 。 您可以在相關聯的資源編輯器或 [屬性視窗](/visualstudio/ide/reference/properties-window)中編輯資源屬性，以自訂此資源識別碼。

> [!NOTE]
> 請勿指定 Visual Studio 保留的資源名稱或識別碼。 保留的名稱為 `DESIGNINFO` 、 `HWB` 和 `TEXTINCLUDE` ，而保留識別碼為 `255` 。

### <a name="to-create-a-resource"></a>建立資源

- 在**資源檢視**中，選取您的 .rc 檔，然後使用 [**編輯**  >  **新增資源**]，並選擇要新增至專案的資源類型。

   > [!TIP]
   > 您也可以用滑鼠右鍵按一下 **資源檢視** 中的 .rc 檔，然後從快捷方式功能表選擇 [ **加入資源** ]。

- 在**方案總管**中，以滑鼠右鍵按一下專案資料夾，選取 [**新增**  >  **資源**]，然後選擇要加入至專案的資源類型。

   > [!NOTE]
   > 如果您的專案中還沒有 .rc 檔，此步驟會建立一個。 接著，您可以重複此步驟，將特定資源類型加入至新的 .rc 檔。

- 在[類別檢視](/visualstudio/ide/viewing-the-structure-of-code)中，以滑鼠右鍵按一下類別，選取 [**新增**  >  **資源**]，然後選擇要加入至專案的資源類型。

- 使用功能表**專案**[  >  **加入資源**]。

## <a name="use-resource-templates"></a>使用資源範本

資源範本是您儲存為 .rct 檔案的自訂資源。 資源範本接著會作為建立資源的起點。 資源範本可節省開發額外資源的時間，或共用功能的資源群組，例如標準控制項或重複的元素。 例如，如果您想要在數個對話方塊中包含包含公司標誌圖示的 [說明] 按鈕，請建立新的對話方塊範本，並使用 [說明] 按鈕和標誌進行自訂。

自訂資源範本之後，請將您的變更儲存在範本資料夾或 include 路徑中指定的位置，讓新的資源範本出現在 [新增 **資源** ] 對話方塊的資源類型下。 您現在可以視需要使用新的資源範本。

> [!NOTE]
> 資源編輯器會自動提供唯一的資源識別碼。 您可以視需要修改 [資源屬性](./resource-editors.md) 。

> [!NOTE]
> 將特定語言的範本檔案放在主要範本目錄的子目錄中。 例如，只提供英文的範本檔案， * \\<資源範本目錄 \> \ 1033*。
>
> Visual Studio 在*\Program Files\Microsoft Visual Studio \<version\> \VC\VCResourceTemplates*、 *\Program FILES\MICROSOFT Visual Studio \<version> \VC\VCResourceTemplates \\<LCID \> * (中搜尋新的 .rct 檔案，例如英文) 的 lcid 1033 或[include 路徑](./how-to-include-resources-at-compile-time.md)上的任何位置。 如果您想要將 .rct 檔案儲存在另一個位置，則必須將位置新增至 include 路徑。

### <a name="to-create-and-use-a-resource-template"></a>建立和使用資源範本

1. 在**方案總管**中，以滑鼠右鍵按一下您的專案，然後選取 [**加入**  >  **新專案**]。

1. 在 [ **範本：** ] 窗格中，選取 [ **資源範本檔 ( .rct) **。

1. 提供新 *.rct* 檔案的名稱和位置，然後選擇 [ **開啟**]。

   新的 *.rct* 檔案會加入至您的專案，並顯示在 **方案總管** 的 [ **Resources** ] 資料夾底下。

1. 按兩下 *.rct* 檔案，在文件視窗中開啟它。 若要加入資源，請在文件視窗中的檔案上按一下滑鼠右鍵，然後選擇 [ **加入資源**]。

   您可以自訂已加入的資源，並儲存 *.rct* 檔。

1. 在 [ **資源檢視** ] 窗格中，以滑鼠右鍵按一下 *.rc* 檔，然後選擇 [ **加入資源**]。

1. 選取資源旁邊的加號 (**+**) ，以展開資源節點，並查看該資源可用的範本。

1. 按兩下您想要使用的範本。

   您可以視需要在其資源編輯器中修改新增的資源。

### <a name="to-convert-an-existing-resource-file-to-a-template"></a>將現有的資源檔轉換成範本

當資源腳本檔案開啟時，在功能表中，**移至 [** 檔案  >  **另存 \<*filename*> **新檔]。 指定位置並選擇 **[確定]**。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源檔](../windows/resource-files-visual-studio.md)<br/>
[如何：管理資源](../windows/how-to-copy-resources.md)<br/>
[如何：在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)<br/>
