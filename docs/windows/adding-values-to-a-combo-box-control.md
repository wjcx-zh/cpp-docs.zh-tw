---
title: 將值加入至下拉式方塊控制項 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.combo
dev_langs:
- C++
helpviewer_keywords:
- combo boxes [C++], Data property
- controls [C++], testing values in combo boxes
- combo boxes [C++], adding values
- combo boxes [C++], previewing values
- Data property
- combo boxes [C++], testing values
ms.assetid: 22a78f98-fada-48b3-90d8-7fa0d8e4de51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 224f52ed9141f302568fe007e7cde4ef609d00ed
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317957"
---
# <a name="adding-values-to-a-combo-box-control"></a>將值加入至下拉式方塊控制項

您可以將值加入下拉式方塊控制項，只要您有 **對話方塊**編輯器中開啟。

> [!TIP]
> 它是個不錯的主意，將所有的值加入至下拉式方塊*之前*大小的方塊中**對話方塊**編輯器中，或者您可能會截斷應該會出現在下拉式方塊控制項的文字。

### <a name="to-enter-values-into-a-combo-box-control"></a>若要在下拉式方塊控制項中輸入值

1. 按一下並選取下拉式方塊控制項。

2. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，向下捲動至**資料**屬性。

   > [!NOTE]
   > 如果您要顯示依類型分組的屬性**資料**會出現在**其他**屬性。

3. 針對 [值] 區域中按一下**資料**屬性並輸入您的資料值，以分號隔開。

   > [!NOTE]
   > 因為空間干擾下拉式清單中的字母排序，請不要將值之間的空格。

4. 按一下  **Enter**當您完成加入值。

放大下拉式方塊的下拉式部分的資訊，請參閱[設定的下拉式方塊和下拉式清單中其大小](setting-the-size-of-the-combo-box-and-its-drop-down-list.md)。

> [!NOTE]
> 您無法將使用此程序的 Win32 專案中的值 (**資料**屬性灰色 Win32 專案)。 因為 Win32 專案不會新增這項功能的程式庫，您必須使用 Win32 專案下拉式方塊以程式設計方式加入值。

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>若要在下拉式方塊中測試值的外觀

1. 輸入中的值之後**資料** 屬性中，按一下**測試**按鈕[對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

   請嘗試整個值清單中向下捲動。 值會出現在輸入中，如同**資料**中的屬性**屬性**視窗。 沒有任何拼字檢查或大小寫。

   按下**Esc**以返回 **對話方塊**編輯器。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)  
[控制項](../mfc/controls-mfc.md)