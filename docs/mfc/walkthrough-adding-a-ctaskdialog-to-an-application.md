---
title: 逐步解說：新增 CTaskDialog 至應用程式
ms.date: 04/25/2019
helpviewer_keywords:
- CTaskDialog, adding
- walkthroughs [MFC], dialogs
ms.assetid: 3a62abb8-2d86-4bec-bdb8-5784d5f9a9f8
ms.openlocfilehash: 8cf2223b2859a2dfa6ecc7582ec2f171a056152c
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64558204"
---
# <a name="walkthrough-adding-a-ctaskdialog-to-an-application"></a>逐步解說：新增 CTaskDialog 至應用程式

本逐步解說介紹 [CTaskDialog Class](../mfc/reference/ctaskdialog-class.md) ，並示範如何將其加入應用程式。

`CTaskDialog`是工作的對話方塊，它會取代 Windows 訊息方塊，在 Windows Vista 或更新版本。 `CTaskDialog` 改進原始訊息方塊並加入功能。 在 Visual Studio 中仍然支援 Windows 訊息方塊。

> [!NOTE]
> 之前的 Windows 版本比 Windows Vista 不支援`CTaskDialog`。 如果您想要向在舊版 Windows 上執行您的應用程式的使用者顯示訊息，您必須編寫替代對話方塊選項。 您可以使用靜態方法 [CTaskDialog::IsSupported](../mfc/reference/ctaskdialog-class.md#issupported) ，在執行階段判斷使用者的電腦是否可以顯示 `CTaskDialog`中的 Windows 訊息方塊。 此外，只有使用 Unicode 程式庫建置應用程式時，才能使用 `CTaskDialog` 。

`CTaskDialog` 支援幾個可收集及顯示資訊的選擇性項目。 例如， `CTaskDialog` 可以顯示命令連結、自訂按鈕、自訂圖示和頁尾。 `CTaskDialog` 也包含幾種方法，可讓您查詢工作對話方塊的狀態，以判斷使用者選取了哪些選擇性項目。

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成此逐步解說：

- Visual Studio 2010 (含) 以後版本

- Windows Vista 或更新版本

## <a name="replacing-a-windows-message-box-with-a-ctaskdialog"></a>以 CTaskDialog 取代 Windows 訊息方塊

下列程序示範 `CTaskDialog`的最基本用法，也就是取代 Windows 訊息方塊。 此範例也會變更已與工作對話方塊建立關聯的圖示。 變更圖示可讓`CTaskDialog`出現相同的 Windows 訊息方塊。

### <a name="to-replace-a-windows-message-box-with-a-ctaskdialog"></a>以 CTaskDialog 取代 Windows 訊息方塊

1. 使用**MFC 應用程式精靈**建立 MFC 應用程式使用所有預設設定。 請參閱[逐步解說：使用新的 MFC Shell 控制項](walkthrough-using-the-new-mfc-shell-controls.md)如需有關如何開啟您的 Visual Studio 版本的精靈。

1. 稱之為*MyProject*。 

1. 使用 **方案總管** 開啟 MyProject.cpp 檔案。

1. 將 `#include "afxtaskdialog.h"` 加入包含清單後面。

1. 尋找 `CMyProjectApp::InitInstance`方法。 在 `return TRUE;` 陳述式前面插入下列幾行程式碼。 此程式碼會建立用於 Windows 訊息方塊或 `CTaskDialog`中的字串。

    ```cpp
    CString message("My message to the user");
    CString dialogTitle("My Task Dialog title");
    CString emptyString;
    ```

1. 將下列程式碼加入步驟 4 的程式碼後面。 此程式碼可確保使用者的電腦支援 `CTaskDialog`。 如果對話方塊不支援，應用程式會改為顯示 Windows 訊息方塊。

    ```cpp
    if (CTaskDialog::IsSupported())
    {

    }
    else
    {
        AfxMessageBox(message);
    }
    ```

1. 將下列程式碼插入步驟 5 之 `if` 陳述式後面的括號之間。 此程式碼會建立 `CTaskDialog`。

    ```cpp
    CTaskDialog taskDialog(message, emptyString, dialogTitle, TDCBF_OK_BUTTON);
    ```

1. 在下一行，加入下列程式碼。 此程式碼會設定警告圖示。

    ```cpp
    taskDialog.SetMainIcon(TD_WARNING_ICON);
    ```

1. 在下一行，加入下列程式碼。 此程式碼會顯示工作對話方塊。

    ```cpp
    taskDialog.DoModal();
    ```

如果您不想，您可以避免步驟 7`CTaskDialog`若要以 Windows 訊息方塊顯示相同的圖示。 如果您有避免該步驟，`CTaskDialog`不會有圖示時的應用程式會顯示它。

編譯並執行應用程式。 應用程式啟動後，會顯示工作對話方塊。

## <a name="adding-functionality-to-the-ctaskdialog"></a>將功能加入 CTaskDialog

下列程序會示範如何將功能加入您在上一個程序中建立的 `CTaskDialog` 。 此範例程式碼會示範如何根據使用者的選取項目來執行特定指示。

### <a name="to-add-functionality-to-the-ctaskdialog"></a>將功能加入 CTaskDialog

1. 巡覽至 [資源檢視] 。 如果您看**資源檢視**，您可以開啟它從**檢視**功能表。

1. 展開 [資源檢視]  ，直到您可以選取 [字串資料表]  資料夾。 將它展開，然後按兩下 [字串資料表]  項目。

1. 捲動至字串資料表底部，然後加入新項目。 將識別碼變更為 `TEMP_LINE1`。 將選項設定為 **[命令列 1]**。

1. 加入另一個新項目。 將識別碼變更為 `TEMP_LINE2`。 將選項設定為 **[命令列 2]**。

1. 巡覽回到 MyProject.cpp。

1. 在 `CString emptyString;`後面，加入下列程式碼：

    ```cpp
    CString expandedLabel("Hide extra information");
    CString collapsedLabel("Show extra information");
    CString expansionInfo("This is the additional information to the user,\nextended over two lines.");
    ```

1. 尋找 `taskDialog.DoModal()` 陳述式，然後將該陳述式取代為下列程式碼。 此程式碼會更新工作對話方塊並加入新的控制項︰

    ```cpp
    taskDialog.SetMainInstruction(L"Warning");
    taskDialog.SetCommonButtons(
        TDCBF_YES_BUTTON | TDCBF_NO_BUTTON | TDCBF_CANCEL_BUTTON);
    taskDialog.LoadCommandControls(TEMP_LINE1, TEMP_LINE2);
    taskDialog.SetExpansionArea(
        expansionInfo, collapsedLabel, expandedLabel);
    taskDialog.SetFooterText(L"This is the a small footnote to the user");
    taskDialog.SetVerificationCheckboxText(L"Remember your selection");
    ```

1. 加入下列這行程式碼，以向使用者顯示工作對話方塊並擷取使用者的選取項目︰

    ```cpp
    INT_PTR result = taskDialog.DoModal();
    ```

1. 將下列程式碼插入 `taskDialog.DoModal()`的呼叫後方： 這段程式碼會處理使用者的輸入︰

    ```cpp
    if (taskDialog.GetVerificationCheckboxState())
    {
        // PROCESS IF the user selects the verification checkbox
    }

    switch (result)
    {
    case TEMP_LINE1:
        // PROCESS IF the first command line
        break;
    case TEMP_LINE2:
        // PROCESS IF the second command line
        break;
    case IDYES:
        // PROCESS IF the user clicks yes
        break;
    case IDNO:
        // PROCESS IF the user clicks no
        break;
    case IDCANCEL:
        // PROCESS IF the user clicks cancel
        break;
    default:
        // This case should not be hit because closing
        // the dialog box results in IDCANCEL
        break;
    }
    ```

在 步驟 9 中的程式碼，取代開頭的註解`PROCESS IF`與您想要在指定的條件下執行的程式碼。

編譯並執行應用程式。 應用程式會顯示使用新控制項和其他資訊的工作對話方塊。

## <a name="displaying-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>顯示 CTaskDialog 而不需要建立 CTaskDialog 物件

下列程序示範如何顯示 `CTaskDialog` ，而不需要先建立 `CTaskDialog` 物件。 此範例延續先前的程序。

### <a name="to-display-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>顯示 CTaskDialog 而不需要建立 CTaskDialog 物件

1. 如果尚未開啟，請開啟 MyProject.cpp 檔案。

1. 巡覽至 `if (CTaskDialog::IsSupported())` 陳述式的右中括號。

1. 緊接在 `if` 陳述式的右中括號前面 ( `else` 區塊前面) 插入下列程式碼：

    ```cpp
    HRESULT result2 = CTaskDialog::ShowDialog(L"My error message",
        L"Error",
        L"New Title",
        TEMP_LINE1,
        TEMP_LINE2);
    ```

編譯並執行應用程式。 應用程式會顯示兩個對話方塊。 第一個對話方塊是來自**將功能加入 CTaskDialog**程序; 第二個對話方塊是來自上一個程序。

這些範例不示範所有可用的選項，如`CTaskDialog`，但應該可以協助您開始著手。 如需此類別的完整說明，請參閱 [CTaskDialog Class](../mfc/reference/ctaskdialog-class.md) 。

## <a name="see-also"></a>另請參閱

[對話方塊](../mfc/dialog-boxes.md)<br/>
[CTaskDialog 類別](../mfc/reference/ctaskdialog-class.md)<br/>
[CTaskDialog::CTaskDialog](../mfc/reference/ctaskdialog-class.md#ctaskdialog)
