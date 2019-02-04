---
title: 編輯多個功能表或功能表命令 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- menu commands [C++], selecting
- menus [C++], selecting
- commands [C++], menu commands
- commands [C++], copying on menus
- menu items, moving
- commands [C++], moving on menus
- menu items, copying
- menu items, deleting
- commands [C++], deleting from menus
- menus [C++], deleting
ms.assetid: b6f17897-2a40-4afd-97d4-a38b7661680b
ms.openlocfilehash: 45e2c4e97dc850b4d6fb13a5526911e4bd5caec2
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703216"
---
# <a name="editing-multiple-menus-or-menu-commands"></a>編輯多個功能表或功能表命令

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="to-select-multiple-menu-commands"></a>選取多個功能表命令

您可以選取多個功能表名稱或功能表命令來執行大量作業，例如刪除或變更屬性。

按住**Ctrl**機碼，請選取您想要的子功能表命令的功能表。

## <a name="to-move-and-copy-menus-and-menu-commands"></a>移動及複製功能表和功能表命令

您可以移動或複製功能表和功能表命令，方法是使用拖放方法或使用捷徑功能表的命令 (在功能表上按一下滑鼠右鍵)。

### <a name="to-move-or-copy-menus-or-menu-commands-using-the-drag-and-drop-method"></a>使用拖放方法移動或複製功能表或功能表命令

1. 將您要移動的項目拖曳或複製到：

   - 目前功能表中的新位置

   - 其他功能表。 (您可以藉由拖曳滑鼠指標停留在上面以瀏覽至其他功能表。)

1. 當插入輔助線顯示想要的位置時，請放下功能表命令。

### <a name="to-move-or-copy-menus-or-menu-commands-using-shortcut-menu-commands"></a>使用捷徑功能表命令移動或複製功能表或功能表命令

1. 在一或多個功能表或功能表命令上按一下滑鼠右鍵。

1. 從捷徑功能表選擇 [ **剪下** ] (以移動) 或 [ **複製**]。

1. 如果您要將項目移到另一個功能表資源或資源指令碼檔案，[另一個視窗中開啟](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

1. 選取您要移動或複製目標的功能表或功能表命令位置。

1. 從捷徑功能表上選擇 [ **貼上**]。 移動或複製的項目會放在您選取的項目之前。

   > [!NOTE]
   > 您也可以拖曳、複製和貼上到其他功能表視窗中的其他功能表。

## <a name="to-delete-a-menu-or-menu-command"></a>刪除功能表或功能表命令

1. 以滑鼠右鍵按一下功能表名稱或命令。

1. 從捷徑功能表選擇 [ **刪除** ]。

   > [!NOTE]
   > 同樣地，您可以使用捷徑功能表來執行其他動作，例如複製、剪下、貼上、插入新項目、插入分隔字元、編輯 ID、以快顯方式檢視、檢查助憶鍵等。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[功能表編輯器](../windows/menu-editor.md)