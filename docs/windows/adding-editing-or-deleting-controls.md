---
title: 如何：在 c + +) 中加入、編輯或刪除控制項 (
ms.date: 02/15/2019
f1_keywords:
- vc.controls.activex
- vc.editors.dialog.insertActiveXControls
helpviewer_keywords:
- Dialog Editor [C++], creating controls
- dialog boxes [C++], adding controls to
- Toolbox [C++], Dialog Editor tab
- controls [C++], types
- syslink controls in dialog boxes
- custom controls [C++], dialog boxes
- controls [C++], standard
- Dialog Editor [C++], creating controls
- controls [C++], adding to dialog boxes
- controls [C++], adding multiple
- dialog box controls [C++], size
- controls [C++], sizing
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
- Insert ActiveX Control dialog box [C++]
- controls [C++], editing properties
- ActiveX controls [C++], properties
- controls [C++], undoing changes
- controls [C++], editing properties
- dialog box controls [C++], editing properties
- dialog box controls [C++], deleting
- controls [C++], deleting
- Dialog Editor [C++], default control events
- controls [C++], default control events
- events [C++], controls
- dialog box controls [C++], events
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog Editor [C++], defining member variables for controls
- controls [C++], troubleshooting
- Dialog Editor [C++], troubleshooting
- dialog boxes [C++], troubleshooting
- InitCommonControls
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 73cef03f-5c8c-456a-87d1-1458dff185cf
ms.openlocfilehash: 90e4eb659de6d1d5ed1488365f6637de2d537e57
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831680"
---
# <a name="how-to-add-edit-or-delete-controls-c"></a>如何：在 c + +) 中加入、編輯或刪除控制項 (

您可以使用 **對話方塊編輯器**，加入、調整大小、編輯和刪除對話方塊中的控制項。 您也可以編輯控制項的屬性，例如其識別碼，或是否在執行時間開始顯示。

當您在**對話方塊編輯器**中工作時，[**對話方塊編輯器**] 索引標籤會出現在 [[工具箱] 視窗](/visualstudio/ide/reference/toolbox)中。 您也可以自訂 [ **工具箱** ] 視窗，以便更容易使用。 如需詳細資訊，請參閱 [使用工具箱](/visualstudio/ide/using-the-toolbox) ，並 [顯示或隱藏 [工具箱] 視窗](showing-or-hiding-the-dialog-editor-toolbar.md)。

> [!TIP]
> 使用 **對話方塊編輯器**時，在許多情況下，您可以選取滑鼠右鍵以顯示常用命令的快捷方式功能表。

## <a name="add-controls"></a>新增控制項

### <a name="to-add-a-control"></a>若要加入控制項

1. 確定對話方塊索引標籤式視窗是編輯器框架中的目前文件。 如果對話方塊不是目前檔，您就不會在 [**工具箱**] 中看到 [**對話方塊編輯器]** 索引標籤。

1. 在 [**工具箱**] 視窗的 [**對話方塊編輯器**] 索引標籤上，選取您要的控制項，然後執行下列其中一項：

   - 在您要放置控制項的位置選取對話方塊，並在您選取的位置中顯示控制項。

   - 將控制項從 [ **工具箱** ] 視窗拖放至對話方塊中的位置。 然後，您可以四處移動控制項，或變更其大小和形狀。

   - 按兩下 [ **工具箱** ] 視窗中的控制項，它就會出現在對話方塊中。 將控制項重新放置到您偏好的位置。

### <a name="to-add-multiple-controls"></a>若要加入多個控制項

1. 按住 **Ctrl** 鍵時，請在 [ **工具箱** ] 視窗中選取控制項。

1. 放開 **Ctrl** 鍵，然後選取對話方塊，然後選取您想要新增特定控制項的次數。

1. 按下 **Esc** 鍵以停止放置控制項。

### <a name="to-size-a-control-while-you-add-it"></a>若要在加入控制項時調整其大小

1. 在 [ **工具箱** ] 視窗中選取控制項。

1. 將顯示為十字線的游標放在您想要讓新控制項左上角的對話方塊上。

1. 選取並按住滑鼠按鍵，在對話方塊上錨定控制項的左上角。 然後將游標向右和向下拖曳，直到控制項是您想要的大小為止。

   > [!NOTE]
   > 您可以錨定您要繪製之控制項的四個角落。 此程式使用左上角作為範例。

1. 放開滑鼠按鈕。 控制項會以您指定的大小，在對話方塊中進行結算。

> [!TIP]
> 您可以藉由移動控制項框線上的調整大小控點，在將控制項拖放到對話方塊之後調整它的大小。 如需詳細資訊，請參閱 [調整個別控制項的大小](../windows/sizing-individual-controls.md)。

### <a name="to-add-a-custom-control"></a>若要加入自訂控制項

您可以將自訂控制項加入對話方塊中。 選取 [**工具箱**] 中的 [**自訂控制項**] 圖示，並將它拖曳至您的對話方塊。 若要加入 `Syslink` 控制項，請加入自訂控制項，然後將控制項的 [ **類別** ] 屬性變更為 `Syslink` 。 此動作會使屬性重新整理，並顯示 `Syslink` 控制項屬性。 如需 MFC 包裝函式類別的詳細資訊，請參閱 [CLinkCtrl](../mfc/reference/clinkctrl-class.md)。

## <a name="edit-controls"></a>編輯控制項

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>編輯控制項或控制項的屬性

1. 在對話方塊中，選取您要修改的控制項。

   > [!NOTE]
   > 如果您選取多個控制項，只能編輯所選控制項的通用屬性。

1. 在 [ [屬性視窗](/visualstudio/ide/reference/properties-window)中，變更控制項的屬性。

   > [!NOTE]
   > 當您將按鈕、選項按鈕或核取方塊控制項的 [ **點陣圖** ] 屬性設定為 [ **True**] 時，就會為您的控制項執行樣式 BS_BITMAP。 如需詳細資訊，請參閱 [按鈕樣式](../mfc/reference/styles-used-by-mfc.md#button-styles)。 如需將點陣圖與控制項建立關聯的範例，請參閱 [CButton：： SetBitmap](../mfc/reference/cbutton-class.md#setbitmap)。 當您在 **對話方塊編輯器**中時，點陣圖不會出現在您的控制項上。

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>復原控制項屬性的變更

1. 請確定控制項在 **對話方塊編輯器**中具有焦點。

1. 移至 [功能表**編輯**  >  **復原**]。 如果焦點不在控制項上，將無法使用 [ **復原** ] 命令。

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>定義對話方塊控制項的成員變數 (非按鈕)

> [!NOTE]
> 此程式只適用于 MFC 專案中的對話方塊控制項。 ATL 專案應該使用新的 [ **Windows 訊息和事件處理常式** ] 對話方塊。 如需詳細資訊，請參閱 [與使用者介面物件相關聯的訊息類型](../mfc/reference/message-types-associated-with-user-interface-objects.md)、 [編輯訊息處理常式](../mfc/reference/editing-a-message-handler.md)，以及 [定義反映訊息的訊息處理常式](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)。

1. 在 [對話方塊編輯器](dialog-editor.md)中，選取控制項。

1. 按下 **Ctrl** 鍵時，按兩下對話方塊控制項。

   [ [加入成員變數] wizard](../ide/add-member-variable-wizard.md) 隨即出現。

1. 在 [ **加入成員變數** ] wizard 中輸入適當的資訊。 如需詳細資訊，請參閱 [對話方塊資料交換](../mfc/dialog-data-exchange.md)。

1. 選取 **[確定** ] 以返回 **對話方塊編輯器**。

> [!TIP]
> 若要從任何對話方塊控制項跳至其現有的處理常式，請按兩下控制項。

您也可以使用 [ [MFC 類別] Wizard](../mfc/reference/mfc-class-wizard.md)中的 [**成員變數**] 索引標籤，加入指定類別的新成員變數，並查看已經定義的成員變數。

## <a name="delete-controls"></a>刪除控制項

在對話方塊中，選取控制項，然後按**Delete**鍵，或移至 [功能表**編輯**  >  **刪除**]。

## <a name="other-issues"></a>其他問題

### <a name="troubleshooting"></a>疑難排解

將通用控制項或 rich edit 控制項新增至對話方塊之後，當您測試對話方塊時，它就不會出現。 或者，對話方塊本身也不會出現。 例如：

1. 建立 Win32 專案，修改應用程式設定，讓您建立 Windows 應用程式， (不是主控台應用程式) 。

1. 在 [資源檢視](how-to-create-a-resource-script-file.md#create-resources)中，按兩下 *.rc* 檔。

1. 在對話方塊選項下，按兩下 [ **關於** ] 方塊。

1. 將 **IP 位址控制項** 新增至對話方塊。

1. 全部儲存並 **重建**。

1. 執行程式。

1. 在對話方塊的 [說明 **] 功能表上** ，選取 [ **關於** ] 命令，並觀察不會顯示任何對話方塊。

目前，當您將下列通用控制項或 rich edit 控制項拖放至對話方塊時， **對話方塊編輯器** 不會自動將程式碼加入至您的專案。 也 Visual Studio 在發生此問題時，不會提供錯誤或警告。 若要修正，請手動加入控制項的程式碼。

:::row:::
   :::column span="":::
      動畫控制 \
      自訂控制項 \
      日期時間選擇器 \
      擴充的下拉式方塊
   :::column-end:::
   :::column span="":::
      快速鍵 \
      IP 位址控制 \
      List Control \
      Month Calendar
   :::column-end:::
   :::column span="":::
      進度控制項 \
      Rich Edit 2.0 Control \
      Rich Edit 控制項 \
      滑桿控制項
   :::column-end:::
   :::column span="":::
      微調控制 \
      選項卡控制 \
      樹狀目錄控制項
   :::column-end:::
:::row-end:::

若要在對話方塊中使用通用控制項，您必須呼叫 [InitCommonControlsEx](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex) ，或在 `AFXInitCommonControls` 建立對話方塊之前呼叫。

若要使用 RichEdit 控制項，您必須呼叫 `LoadLibrary` 。 如需詳細資訊，請參閱 Windows SDK 中的 [Rich Edit 控制項](/windows/win32/Controls/about-rich-edit-controls) 和 [rich Edit 控制項的總覽](../mfc/overview-of-the-rich-edit-control.md)。

> [!NOTE]
> 若要將 RichEdit 控制項與 MFC 搭配使用，您必須先呼叫 [AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2) 載入 RichEdit 2.0 控制項 ( # A0) ，或呼叫 [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) 以載入舊版 RichEdit 1.0 控制項 ( # A1) 。
>
> 您可以使用目前的 [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) 類別搭配舊版 RichEdit 1.0 控制項，但其 `CRichEditCtrl` 設計目的是為了支援 RichEdit 2.0 控制項。 由於 RichEdit 1.0 和 RichEdit 2.0 很類似，因此大部分的方法都可以運作。 不過，1.0 和2.0 控制項之間有一些差異，因此某些方法可能無法正常運作或無法正常運作。

### <a name="activex-controls"></a>ActiveX 控制項

Visual Studio 可讓您在您的對話方塊中插入 ActiveX 控制項。 如需詳細資訊，請參閱 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md) 和 [ActiveX 控制項容器](../mfc/activex-control-containers.md)。

[ **插入 Activex 控制項** ] 對話方塊可讓您在使用 [對話方塊編輯器](dialog-editor.md)時，將 ActiveX 控制項插入對話方塊中。 此對話方塊包含下列屬性：

|屬性|描述|
|---|---|
|**ActiveX 控制項**|顯示 ActiveX 控制項的清單。<br/><br/>從這個對話方塊插入控制項不會產生包裝函式類別。 如果您需要包裝函式類別，請使用 [類別檢視](/visualstudio/ide/viewing-the-structure-of-code) 建立一個包裝函式類別，請參閱 [加入類別](../ide/adding-a-class-visual-cpp.md)。<br/><br/>如果 ActiveX 控制項未出現在此對話方塊中，請嘗試根據廠商的指示來安裝控制項。|
|**路徑**|顯示找到 ActiveX 控制項的檔案。|

> [!CAUTION]
> 在您的系統上散發所有的 ActiveX 控制項可能不合法。 請參閱已安裝控制項或與軟體公司聯繫之軟體的授權合約。

#### <a name="to-add-an-activex-control"></a>加入 ActiveX 控制項

1. 在 **對話方塊編輯器**中開啟對話方塊。

1. 以滑鼠右鍵按一下對話方塊主體內的任何位置，然後選取 [ **插入 ActiveX 控制項**]。

   [ **插入 ActiveX 控制項** ] 對話方塊隨即出現，顯示您系統上的所有 ActiveX 控制項。 ActiveX 控制項檔案的路徑會顯示在對話方塊的底部。

1. 選取您要新增至對話方塊的控制項，然後選擇 **[確定]**。

   該控制項會出現在對話方塊中。您可以像處理其他控制項般地加以編輯，或為其建立處理常式。

> [!TIP]
> 您可以使用 **對話方塊編輯器** 中的快捷方式功能表，將已註冊的 activex 控制項快速加入至對話方塊，或嘗試將 activex 控制項加入 [ **工具箱** ] 視窗中，以方便存取。

#### <a name="to-edit-properties-for-an-activex-control"></a>編輯 ActiveX 控制項的屬性

獨立廠商提供的 ActiveX 控制項可能會有自己的屬性和特性。 這些屬性會顯示在 [ **屬性** ] 視窗中。 ActiveX 控制項的寫入器所建立的任何屬性頁面都會顯示在 [ **屬性頁** ] 對話方塊中。  (若要查看特定 ActiveX 控制項的**屬性頁**，請在[屬性視窗](/visualstudio/ide/reference/properties-window)) 中選取 [**屬性頁**] 按鈕。

- 選取 [ **ActiveX**控制項]，然後移至 [功能表**視圖**]  >  **屬性頁**來查看屬性。 在屬性頁中視需要進行變更。

   ActiveX 控制項的 [屬性] 頁面中會顯示各種索引標籤，這取決於 ActiveX 控制項的一部分屬性工作表。

> [!NOTE]
> 此程式適用于使用 [屬性] 頁面來編輯 ActiveX 控制項。 您也可以在 [新增 **屬性** ] 視窗中流覽和編輯 ActiveX 屬性。

## <a name="requirements"></a>規格需求

Win32

## <a name="see-also"></a>另請參閱

[管理對話方塊控制項](controls-in-dialog-boxes.md)<br/>
[How To： Layout 控制項](arrangement-of-controls-on-dialog-boxes.md)<br/>
[如何：定義控制項存取和值](defining-mnemonics-access-keys.md)

<!-- excluded links
[Mapping Messages to Functions](../mfc/reference/mapping-messages-to-functions.md)<br/>
[Adding Functionality with Code Wizards](../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Adding a Class](../ide/adding-a-class-visual-cpp.md)<br/>
[Adding a Member Function](../ide/adding-a-member-function-visual-cpp.md)<br/>
[Adding a Member Variable](../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Overriding a Virtual Function](../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC Message Handler](../mfc/reference/adding-an-mfc-message-handler.md)
[Declaring a Variable Based on Your New Control Class](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)<br/>
-->
