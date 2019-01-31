---
title: 檢視及加入 ActiveX 控制項加入對話方塊 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.controls.activex
- vc.editors.dialog.insertActiveXControls
helpviewer_keywords:
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
- Insert ActiveX Control dialog box [C++]
- controls [C++], editing properties
- ActiveX controls [C++], properties
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
ms.openlocfilehash: 139407ec1d4e1bfad6bb06854dc24b86ce7014e8
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293607"
---
# <a name="viewing-and-adding-activex-controls-to-a-dialog-box-c"></a>檢視及加入 ActiveX 控制項加入對話方塊 （c + +）

Visual Studio 可讓您在您的對話方塊中插入 ActiveX 控制項。

**插入 ActiveX 控制項**對話方塊可讓您插入您的對話方塊中的 ActiveX 控制項，同時使用[對話方塊編輯器](../windows/dialog-editor.md)。 此對話方塊包含下列屬性：

|屬性|描述|
|---|---|
|**ActiveX 控制項**|會顯示一份 Active X 控制項。 從這個對話方塊中插入控制項不會產生包裝函式類別。 如果您需要的包裝函數類別，使用[類別檢視](/visualstudio/ide/viewing-the-structure-of-code)若要建立一個 (如需詳細資訊，請參閱[加入類別](../ide/adding-a-class-visual-cpp.md))。 如果 Active X 控制項不會出現在這個對話方塊中，再次嘗試安裝控制項根據廠商的指示。|
|**路徑**|顯示 ActiveX 控制項所在的檔案。|

您可以放置在控制項**工具箱**視窗以方便存取。 如需詳細資訊，請參閱[工具箱](/visualstudio/ide/reference/)。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="to-see-the-activex-controls-you-have-available"></a>查看您可使用的 ActiveX 控制項

1. 在 [對話方塊] 編輯器中開啟對話方塊。

1. 以滑鼠右鍵按一下任何位置 對話方塊中的主體中。

1. 在快速鍵功能表中，選取**插入 ActiveX 控制項**。

   **插入 ActiveX 控制項** 對話方塊隨即出現，顯示您系統上的所有 ActiveX 控制項。 ActiveX 控制項檔案的路徑會顯示在對話方塊的底部。

## <a name="to-add-an-activex-control-to-a-dialog-box"></a>在對話方塊中加入 ActiveX 控制項

1. 在 **插入 ActiveX 控制項**對話方塊方塊中，選取您想要新增到您的對話方塊中，然後選取的控制**確定**。

   該控制項會出現在對話方塊中。您可以像處理其他控制項般地加以編輯，或為其建立處理常式。

   > [!NOTE]
   > 您可以將 ActiveX 控制項加入 [[工具箱] 視窗](/visualstudio/ide/reference/toolbox)。

   > [!CAUTION]
   > 在您的系統上散發所有的 ActiveX 控制項可能不合法。 請參閱安裝這些控制項之軟體的授權合約，或連絡軟體公司。

   您可以放置在控制項**工具箱**視窗以方便存取。 如需詳細資訊，請參閱[工具箱](/visualstudio/ide/reference/toolbox)。

## <a name="to-edit-properties-for-an-activex-control"></a>若要編輯 ActiveX 控制項的屬性

獨立廠商所提供的 ActiveX 控制項可能都配有其自己的屬性和特性的。 適用於 ActiveX 控制項的屬性會顯示在**屬性**視窗。 此外，ActiveX 控制項的寫入器所建立的任何屬性頁面會顯示在**屬性頁** 對話方塊 (若要檢視 **屬性頁**對於特定的 ActiveX 控制項中，按一下 [ **屬性頁**按鈕[屬性] 視窗](/visualstudio/ide/reference/properties-window))。

各種索引標籤會顯示在屬性頁面中的 ActiveX 控制項，視屬性工作表做為 ActiveX 控制項的一部分，而定。

> [!NOTE]
> 下列程序適用於使用屬性頁編輯 ActiveX 控制項。 您也可以瀏覽並編輯 ActiveX 屬性中的新**屬性**視窗。

1. 選取  **ActiveX**控制項。

1. 在上**檢視**功能表上，選取** 屬性頁**檢視內容。

1. 視需要在 [屬性] 頁面中，請進行變更。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)<br/>
[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[ActiveX 控制項容器](../mfc/activex-control-containers.md)<br/>
[檢視 ActiveX 控制項以及將 ActiveX 控制項新增至對話方塊](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)<br/>
[工具箱、對話方塊編輯器索引標籤](../windows/dialog-editor-tab-toolbox.md)<br/>
[資源檔](../windows/resource-files-visual-studio.md)<br/>
