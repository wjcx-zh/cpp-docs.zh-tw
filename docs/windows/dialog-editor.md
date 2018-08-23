---
title: 對話方塊編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.dialog
- vc.editors.dialog.F1
dev_langs:
- C++
helpviewer_keywords:
- resource editors, Dialog editor
- editors, dialog boxes
- Dialog editor
- dialog boxes, editing
ms.assetid: d94884ef-2cca-49d8-9b58-775f34848134
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 39c34487941ee45f91883ed91b1faa2c93973cfe
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601720"
---
# <a name="dialog-editor"></a>對話方塊編輯器

** 對話方塊**編輯器可讓您建立或編輯對話方塊資源。 您開啟對話方塊編輯器中的對話方塊的.rc 檔上按兩下**資源檢視** 視窗 (**檢視** > **資源檢視**)。 請注意，**資源檢視**不適用於 Express 版本。

建立新對話方塊 (或對話方塊範本) 的前幾個步驟之一，是在對話方塊中加入控制項。 在 [ **] 對話方塊**編輯器中，您可以安排控制項配合特定大小、 圖形或對齊方式，或您可以移動它們大約在對話方塊內順利運作。 刪除控制項也很容易。

您可以將對話方塊儲存成範本，以便重複使用。 您也可以輕鬆地在設計對話方塊和編輯其實作程式碼之間來回切換。

在對話方塊編輯器中也可以編輯單一或多個控制項的屬性。 您可以變更定位順序，也就是取得控制項的順序聚焦在何時 **索引標籤**按鍵，或者您可以定義便捷鍵 （按鍵組合），可讓使用者選擇使用鍵盤的控制項。 如需預設的便捷鍵清單，請參閱 [對話方塊編輯器的快速鍵](../windows/accelerator-keys-for-the-dialog-editor.md)。

** 對話方塊**編輯器也可讓您使用自訂控制項，包括 ActiveX 控制項。 此外，您可以編輯 [表單檢視](../mfc/reference/cformview-class.md)、 [資料錄檢視表](../data/record-views-mfc-data-access.md)或 [對話方塊列](../mfc/dialog-bars.md)。

從 Visual Studio 2015 開始，您可以使用對話方塊編輯器定義動態配置，其會指定控制項移動及調整大小，當使用者調整對話方塊的方式。 如需詳細資訊，請參閱 [Dynamic Layout](../mfc/dynamic-layout.md)。

- [建立新的對話方塊](../windows/creating-a-new-dialog-box.md)

- [建立使用者在執行階段無法結束的對話方塊](../windows/creating-a-dialog-box-that-users-cannot-exit.md)

- [顯示或隱藏對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)

- [切換對話方塊編輯器和程式碼](../windows/switching-between-dialog-box-controls-and-code.md)

- [對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)

- [加入對話方塊控制項的事件處理常式](../windows/adding-event-handlers-for-dialog-box-controls.md)

- [測試對話方塊](../windows/testing-a-dialog-box.md)

- [對話方塊編輯器的快速鍵](../windows/accelerator-keys-for-the-dialog-editor.md)

- [對話方塊編輯器的疑難排解](../windows/troubleshooting-the-dialog-editor.md)

   > [!TIP]
   > 在使用時 **對話方塊**編輯器，在許多情況下，您可以按一下滑鼠右鍵顯示常用命令的捷徑功能表。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)  
[控制項](../mfc/controls-mfc.md)  
[控制項類別](../mfc/control-classes.md)  
[對話方塊類別](../mfc/dialog-box-classes.md)  
[對話方塊控制項和變數類型](../ide/dialog-box-controls-and-variable-types.md)