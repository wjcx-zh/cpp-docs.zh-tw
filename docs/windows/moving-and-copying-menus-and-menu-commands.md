---
title: 移動和複製功能表和功能表命令 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- commands, copying on menus
- menu items, moving
- commands, moving on menus
- menu items, copying
ms.assetid: 1d8df535-9922-4579-a9c2-37aeac1856eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d7933aeb5b9b12e761c684a1a9b62c4201ef4bdb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204834"
---
# <a name="moving-and-copying-menus-and-menu-commands"></a>移動和複製功能表和功能表命令

您可以移動或複製功能表和功能表命令，方法是使用拖放方法或使用捷徑功能表的命令 (在功能表上按一下滑鼠右鍵)。

### <a name="to-move-or-copy-menus-or-menu-commands-using-the-drag-and-drop-method"></a>使用拖放方法移動或複製功能表或功能表命令

1. 將您要移動的項目拖曳或複製到：

   - 目前功能表中的新位置

   - 其他功能表。 (您可以藉由拖曳滑鼠指標停留在上面以瀏覽至其他功能表。)

2. 當插入輔助線顯示想要的位置時，請放下功能表命令。

### <a name="to-move-or-copy-menus-or-menu-commands-using-shortcut-menu-commands"></a>使用捷徑功能表命令移動或複製功能表或功能表命令

1. 在一或多個功能表或功能表命令上按一下滑鼠右鍵。

2. 從捷徑功能表選擇 [ **剪下** ] (以移動) 或 [ **複製**]。

3. 如果將項目移至另一個功能表資源或資源指令碼檔案， [在另一個視窗中開啟它](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

4. 選取您要移動或複製目標的功能表或功能表命令位置。

5. 從捷徑功能表上選擇 [ **貼上**]。 移動或複製的項目會放在您選取的項目之前。

   > [!NOTE]
   > 您也可以拖曳、複製和貼上到其他功能表視窗中的其他功能表。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[功能表編輯器](../windows/menu-editor.md)