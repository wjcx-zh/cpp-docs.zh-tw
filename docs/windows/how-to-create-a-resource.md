---
title: HOW TO：建立資源 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vs.resourceview.F1
- vc.editors.insertresource
- vc.editors.newcustomresource
helpviewer_keywords:
- toolbars [C++], resources
- resource toolbars
- resources [C++], creating
- resources [C++], viewing
- Resource View window
- resources [C++], adding
- Add Resource dialog box [C++]
- Custom Resource Type dialog box [C++]
ms.assetid: aad44914-9145-45a3-a7d8-9de89b366716
ms.openlocfilehash: fdf158bab7894497dbcfb147eb2c6e061879be75
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2019
ms.locfileid: "55764047"
---
# <a name="how-to-create-a-resource-c"></a>HOW TO：建立資源 （c + +）

**資源檢視**視窗會顯示在您的專案中包含的資源檔。 展開最上層資料夾 (例如，Project1.rc) 會顯示該.rc 檔中的資源類型。 展開每個資源類型會顯示該類型的個別資源。

> [!NOTE]
> 這項資訊不適用於通用 Windows 平台應用程式中的資源。 如有關的詳細資訊，請參閱 <<c0> [ 應用程式資源和資源管理系統](/windows/uwp/app-resources/)。

> [!NOTE]
> **資源檢視**在 Express 版中不支援。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。

> [!NOTE]
> 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

**資源檢視** 視窗使用**加入資源**對話方塊，即可將資源新增至 c + + Windows 桌面應用程式專案。 此對話方塊具有下列屬性：

|屬性|描述|
|---|---|
|**資源類型**|指定您想要建立的資源種類。<br/><br/>您可以展開資料指標和對話方塊資源類別來顯示其他資源。 這些資源位於 Visual Studio...\Microsoft `version`\VC\VCResourceTemplates\\< LCID\>\mfc.rct。 如果您加入.rct 檔案，您必須將它們放在這個目錄中，或者您必須指定[include 路徑](../windows/how-to-specify-include-directories-for-resources.md)它們。 如此，那些檔案中的資源將會顯示在適當分類底下的第二層。 沒有任何預先設定的限制，您可以加入的.rct 檔案數目。<br/><br/>樹狀目錄控制項最上層所顯示的資源，是 Visual Studio 所提供的預設資源。|
|**新增**|建立資源，根據您已選取中的型別**資源類型** 方塊中。 資源會在適當的編輯器中開啟。 例如，如果您建立對話方塊資源時，它會在中開啟[對話方塊編輯器](../windows/dialog-editor.md)。|
|**Import**|會開啟**匯入**對話方塊中，在其中您可以瀏覽至資源您想要匯入至您目前的專案。 您可以匯入點陣圖、圖示、游標、HTML 資源檔、音效 (.WAV) 資源檔或自訂資源檔。|
|**自訂**|會開啟**新的自訂資源**對話方塊中，您可以在其中建立自訂的資源。 自訂資源只能在二進位編輯器中編輯。|

**新的自訂資源**對話方塊可讓您在 c + + 專案中建立新的自訂資源。 此對話方塊具有下列屬性：

|屬性|描述|
|---|---|
|**資源類型**|提供文字方塊，讓您輸入的自訂資源類型名稱。 Visual c + + 自動將單字的名稱，當您結束**新的自訂資源** 對話方塊。|

當您建立新的資源時，Visual c + + 會指派一個唯一的名稱，比方說， `IDD_Dialog1`。 您可以在相關聯的資源編輯器中或在 [ [屬性視窗](/visualstudio/ide/reference/properties-window)] 中編輯資源的屬性，以自訂此資源 ID。

您可以建立資源，為新的預設資源 （不以範本為基礎的資源），或為資源，模仿[範本](../windows/how-to-use-resource-templates.md)。

> [!NOTE]
> 未指定資源名稱或保留 Visual Studio 的識別碼。 保留的名稱為 DESIGNINFO、 HWB 和 TEXTINCLUDE，而保留的 ID 為 255。

## <a name="to-open-the-resource-view-window"></a>開啟 [資源檢視] 視窗。

選取 **資源檢視**上**檢視**功能表。

   \-或-

按下**Ctrl** + **Shift** + **E**。

> [!TIP]
> 您可以以滑鼠右鍵按一下**資源檢視**視窗來啟動命令的捷徑功能表。 您也可以按兩下標題列來停駐或取消停駐視窗。 在標題列上按一下滑鼠右鍵可會提供其他命令，而可讓您控制視窗的行為。 如需詳細資訊，請參閱 < [Windows Management](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

## <a name="to-create-a-new-resource-in-resource-view"></a>在資源檢視中建立新的資源

1. 使用焦點設在.rc 檔中**資源檢視**，選取**編輯**功能表，然後選擇 **加入資源**(或以滑鼠右鍵按一下.rc 檔中的**資源檢視** ，然後選擇 **加入資源**從快顯功能表)。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 在 **加入資源**對話方塊方塊中，選擇您想要新增至您的專案資源的類型。

## <a name="to-create-a-new-resource-in-solution-explorer"></a>在方案總管中建立新的資源

1. 在 [ **方案總管**] 中，以滑鼠右鍵按一下專案資料夾並選擇 [ **加入**]，然後在捷徑功能表上按一下 [ **加入資源** ]。

   如果您在專案中還沒有.rc 檔，此步驟會建立一個。 接著，您可以重複此步驟，將特定資源類型加入至新的 .rc 檔。

2. 在 **加入資源**對話方塊方塊中，選擇您想要新增至您的專案資源的類型。

## <a name="to-create-a-new-resource-in-class-view"></a>在類別檢視中建立新的資源

1. 在 [類別檢視](/visualstudio/ide/viewing-the-structure-of-code)，以滑鼠右鍵按一下您的類別，然後選擇 **新增**，然後選取**加入資源**從捷徑功能表。

2. 在 **加入資源**對話方塊方塊中，選擇您想要新增至您的專案資源的類型。

## <a name="to-create-a-new-resource-from-the-project-menu"></a>從專案功能表建立新的資源

從 [ **專案** ] 功能表中，選擇 [ **加入資源**]。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[使用資源檔](../windows/working-with-resource-files.md)<br/>
[資源檔](../windows/resource-files-visual-studio.md)<br/>
[資源編輯器](../windows/resource-editors.md)<br/>
