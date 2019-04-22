---
title: 如何：加入、 編輯或刪除控制項 (C++)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog.dialog
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
ms.openlocfilehash: 2e3e671cd92313ad120d2cd6aae3f7e815e09e65
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025360"
---
# <a name="how-to-add-edit-or-delete-controls-c"></a>如何：加入、 編輯或刪除控制項 (C++)

使用**對話方塊編輯器**、 您可以新增、 調整大小、 編輯和刪除在對話方塊中的控制項。 您也可以編輯的控制項，例如其識別碼、 屬性或它是否一開始出現在執行階段。

**對話方塊編輯器**索引標籤會出現在[工具箱視窗](/visualstudio/ide/reference/toolbox)當您處理**對話方塊編輯器**。 您也可以自訂**工具箱**，方便使用的視窗。 如需詳細資訊，請參閱 <<c0> [ 使用工具列](/visualstudio/ide/using-the-toolbox)並[顯示或隱藏 [工具箱] 視窗](showing-or-hiding-the-dialog-editor-toolbar.md)。

> [!TIP]
> 在使用時**對話方塊編輯器**，在許多情況下，您可以選取滑鼠右鍵顯示常用命令的捷徑功能表。

## <a name="add-controls"></a>加入控制項

### <a name="to-add-a-control"></a>若要加入控制項

1. 確定對話方塊索引標籤式視窗是編輯器框架中的目前文件。 如果對話方塊不是目前的文件，您不會看到**對話方塊編輯器索引標籤**中**工具箱**。

1. 在 [**對話方塊編輯器**索引標籤**工具箱**] 視窗中，選取您想要的控制項，然後：

   - 選取您想要將控制項放置位置的對話方塊中，控制項就會出現您所選取的位置。

   - 將拖放控制項**工具箱**視窗的位置，在您的對話方塊中，您可以再移動控制項或變更其大小和形狀。

   - 按兩下中的控制項**工具箱**視窗中，而且會出現在對話方塊中，然後調整控制項的位置，以您偏好的位置。

### <a name="to-add-multiple-controls"></a>若要將多個控制項

1. 按住**Ctrl**機碼，請選取中的控制項**工具箱**視窗。

1. 發行**Ctrl**鍵並選取 [] 對話方塊中，您想要新增之特定控制項的次數。

1. 按下**Esc**來停止放置控制項。

### <a name="to-size-a-control-while-you-add-it"></a>若要調整控制項的大小，而您將它加入

1. 選取的控制項**工具箱**視窗。

1. 將游標顯示交叉線，為您想要在您的對話方塊上的新控制項的左上角的位置。

1. 選取並按住滑鼠按鈕，即可在對話方塊中，控制項的左上角的錨點，然後將游標拖曳至右和向下直到控制項是您想要的大小。

   > [!NOTE]
   > 您可以錨定任何您正在繪製之控制項的四個邊角。 此程序會使用左上角，做為範例。

1. 放開滑鼠按鈕。 控制項置於對話方塊中，您所指定的大小。

> [!TIP]
> 您可以調整控制項的大小之後它拖放到對話方塊中移動控制項框線的縮放控點。 如需詳細資訊，請參閱 <<c0> [ 調整個別控制項](../windows/sizing-individual-controls.md)。

### <a name="to-add-a-custom-control"></a>若要加入自訂控制項

您可以將自訂控制項加入對話方塊中選取**自訂控制項**中的圖示**工具箱**將它拖曳至您的對話方塊。 若要新增**Syslink**控制項，加入自訂控制項，然後變更控制項的**類別**屬性設**Syslink**。 此動作會導致要重新整理和顯示的屬性**Syslink**控制屬性。 如需 MFC 包裝函式類別的資訊，請參閱[CLinkCtrl](../mfc/reference/clinkctrl-class.md)。

## <a name="edit-controls"></a>編輯控制項

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>若要編輯的控制項或控制項屬性

1. 在對話方塊中，選取您想要修改的控制項。

   > [!NOTE]
   > 如果您選取多個控制項時，就可以編輯只有選取的控制項通用的屬性。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，變更您的控制項的屬性。

   > [!NOTE]
   > 當您設定**點陣圖**按鈕、 選項按鈕或等於的核取方塊控制項內容 **，則為 True**，為您的控制項實作 BS_BITMAP 樣式。 如需詳細資訊，請參閱 <<c0> [ 按鈕樣式](../mfc/reference/styles-used-by-mfc.md#button-styles)。 如需範例的關聯控制項的點陣圖，請參閱[CButton::SetBitmap](../mfc/reference/cbutton-class.md#setbitmap)。 點陣圖不會出現在您的控制項中**對話方塊編輯器**。

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>若要復原變更控制項的屬性

1. 請確定且焦點在控制項**對話方塊編輯器**。

1. 移至功能表**編輯** > **復原**。 如果焦點在控制項上，不**復原**命令將會無法使用。

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>定義對話方塊控制項的成員變數 (非按鈕)

> [!NOTE]
> 此程序只適用於 MFC 專案中的對話方塊控制項。 ATL 專案應使用**新的 Windows 訊息和事件處理常式** 對話方塊。 如需詳細資訊，請參閱 <<c0> [ 使用者介面物件與相關聯的訊息類型](../mfc/reference/message-types-associated-with-user-interface-objects.md)，[編輯訊息處理常式](../mfc/reference/editing-a-message-handler.md)，和[訊息處理常式定義反映訊息](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

1. 在 [對話方塊編輯器](../windows/dialog-editor.md)，在選取的控制項。

1. 同時按下**Ctrl**機碼，請按兩下對話方塊控制項。

   [加入成員變數精靈](../ide/add-member-variable-wizard.md)隨即出現。

1. 輸入中的相關資訊**加入成員變數**精靈。 如需詳細資訊，請參閱 <<c0> [ 對話資料交換](../mfc/dialog-data-exchange.md)。

1. 選取  **確定**以返回**對話方塊編輯器**。

> [!TIP]
> 若要從任何對話方塊控制項跳至其現有的處理常式，請按兩下控制項。

您也可以使用**成員變數**索引標籤中[MFC 類別精靈](../mfc/reference/mfc-class-wizard.md)，新增新的成員變數，指定的類別，並檢視已定義的成員變數。

## <a name="delete-controls"></a>刪除控制項

在對話方塊中，選取控制項，然後按**刪除**鍵，或移至功能表**編輯** > **刪除**。

## <a name="other-issues"></a>其他問題

### <a name="troubleshooting"></a>疑難排解

通用控制項或 rich edit 控制項加入對話方塊中之後, 則不會顯示當您測試對話方塊中，或本身不會出現對話方塊，例如：

1. 建立 Win32 專案中，修改應用程式設定，讓您建立 Windows 應用程式 （而不將主控台應用程式）。

1. 在 [資源檢視](how-to-create-a-resource-script-file.md#create-resources)，按兩下 *.rc*檔案。

1. 在 對話方塊 選項中，按兩下**關於** 方塊中。

1. 新增**IP 位址控制項**對話方塊中。

1. 儲存並**重建所有**。

1. 執行此程式。

1. 在對話方塊中的**幫助**功能表上，選取**有關**命令並觀察沒有對話方塊隨即出現。

目前，**對話方塊編輯器**不會自動將程式碼加入您的專案時或您拖放的下列通用控制項 rich edit 控制項的對話方塊。 也沒有 Visual Studio 提供錯誤或警告時就會發生此問題。 若要修正，以手動方式加入控制項的程式碼。

||||
|-|-|-|
|滑桿控制項|樹狀目錄控制項|日期時間選擇器|
|微調控制項|索引標籤控制項|月份的行事曆|
|進度控制項|動畫控制項|IP 位址控制項|
|熱鍵|Rich Edit 控制項|擴充的下拉式方塊|
|清單控制項|Rich Edit 2.0 控制項|自訂控制項|

若要使用通用控制項 對話方塊上的，您必須呼叫[InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex)或`AFXInitCommonControls`建立對話方塊之前。

若要使用 RichEdit 控制項，您必須呼叫`LoadLibrary`。 如需詳細資訊，請參閱 <<c0> [ 關於 Rich Edit 控制項](/windows/desktop/Controls/about-rich-edit-controls)Windows SDK 中並[Rich Edit 控制項的概觀](../mfc/overview-of-the-rich-edit-control.md)。

> [!NOTE]
> 若要使用 RichEdit 控制項與 MFC，您必須先呼叫[AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2)載入 RichEdit 2.0 控制項 (RICHED20。DLL)，或呼叫[AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit)載入較舊的 RichEdit 1.0 控制項 (RICHED32。DLL)。
>
> 您可以使用目前[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)類別與較舊的 RichEdit 1.0 控制項，但`CRichEditCtrl`只設計來支援 RichEdit 2.0 控制項。 RichEdit 1.0 和 RichEdit 2.0 很類似，因為大部分的方法就會運作。 不過，有一些差異 1.0 及 2.0 控制項，因此有些方法可能會無法正確運作，或完全無法運作。

### <a name="activex-controls"></a>ActiveX 控制項

Visual Studio 可讓您在您的對話方塊中插入 ActiveX 控制項。 如需詳細資訊，請參閱 < [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)並[ActiveX 控制項容器](../mfc/activex-control-containers.md)。

**插入 ActiveX 控制項**對話方塊可讓您插入您的對話方塊中的 ActiveX 控制項，同時使用[對話方塊編輯器](../windows/dialog-editor.md)。 此對話方塊包含下列屬性：

|屬性|描述|
|---|---|
|**ActiveX 控制項**|顯示 ActiveX 控制項的清單。<br/><br/>從這個對話方塊中插入控制項不會產生包裝函式類別。 如果您需要的包裝函數類別，使用[類別檢視](/visualstudio/ide/viewing-the-structure-of-code)若要建立一個，請參閱[加入類別](../ide/adding-a-class-visual-cpp.md)。<br/><br/>如果 ActiveX 控制項未出現在這個對話方塊中，再次嘗試安裝控制項根據廠商的指示。|
|**路徑**|顯示 ActiveX 控制項所在的檔案。|

> [!CAUTION]
> 在您的系統上散發所有的 ActiveX 控制項可能不合法。 請參閱安裝這些控制項之軟體的授權合約，或連絡軟體公司。

#### <a name="to-add-an-activex-control"></a>若要加入 ActiveX 控制項

1. 開啟對話方塊的 **對話方塊編輯器**。

1. 以滑鼠右鍵按一下 [] 對話方塊中的主體中的任何位置，然後選取**插入 ActiveX 控制項**。

   **插入 ActiveX 控制項** 對話方塊隨即出現，顯示您系統上的所有 ActiveX 控制項。 ActiveX 控制項檔案的路徑會顯示在對話方塊的底部。

1. 選取您想要新增至您的對話方塊中，然後選擇的控制項**確定**。

   該控制項會出現在對話方塊中。您可以像處理其他控制項般地加以編輯，或為其建立處理常式。

> [!TIP]
> 您可以使用中的捷徑功能表**對話方塊編輯器**快速已註冊的 ActiveX 控制項加入對話方塊中，或嘗試加入 ActiveX 控制項，以**工具箱**視窗以方便存取。

#### <a name="to-edit-properties-for-an-activex-control"></a>若要編輯 ActiveX 控制項的屬性

獨立廠商所提供的 ActiveX 控制項可能都配有其自己的屬性和特性的。 這些屬性會顯示在**屬性**視窗中，包括 ActiveX 控制項的寫入器所建立的頁面會顯示在任何屬性**屬性頁**對話方塊 （若要檢視**屬性頁**特定的 ActiveX 控制項中，選取** 屬性頁**按鈕[屬性 視窗](/visualstudio/ide/reference/properties-window))。

- 選取 [ **ActiveX**控制項，並移至功能表**檢視** > **] 屬性頁**來檢視屬性。 視需要在 [屬性] 頁面中，請進行變更。

   各種索引標籤會顯示在屬性頁面中的 ActiveX 控制項，視屬性工作表做為 ActiveX 控制項的一部分，而定。

> [!NOTE]
> 此程序適用於使用屬性頁編輯 ActiveX 控制項。 您也可以瀏覽並編輯 ActiveX 屬性中的新**屬性**視窗。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[管理對話方塊控制項](controls-in-dialog-boxes.md)<br/>
[如何：版面配置控制項](arrangement-of-controls-on-dialog-boxes.md)<br/>
[如何：定義控制項存取與值](defining-mnemonics-access-keys.md)<br/>

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