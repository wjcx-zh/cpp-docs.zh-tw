---
title: 選取多個控制項 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog editor, selecting controls
- dialog box controls, selecting in editor
- controls [C++], selecting
- controls [C++], removing from groups
ms.assetid: efbdbade-0a3a-4328-b36e-a6376c06e8de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 72daa8e4bebfb8a3483c26a25c1f1d253faee8c2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611978"
---
# <a name="selecting-multiple-controls"></a>選取多個控制項

### <a name="to-select-multiple-controls"></a>若要選取多個控制項

1. 在  [[工具箱] 視窗](/visualstudio/ide/reference/toolbox)，選取**指標**工具。

2. 拖曳指標以繪製您想要在您的對話方塊中選取的控制項周圍的選取方塊。

   當您放開滑鼠按鈕時，所有控制項內、 交集與選取方塊已選取。

   \-或-

- 按住**Shift**鍵，然後按一下您想要在選取項目中包含的控制項。

   \-或-

- 按住**Ctrl**鍵，然後按一下您想要在選取項目中包含的控制項。

### <a name="to-remove-a-control-from-a-group-of-selected-controls-or-to-add-a-control-to-a-group-of-selected-controls"></a>若要移除的一組選取的控制項的控制項，或將控制項新增至選取的控制項的群組

1. 使用選取的控制項群組，請按住**Shift**鍵，然後按一下您想要移除或加入到現有的選取範圍的控制項。

   > [!NOTE]
   > 按住**Ctrl**鍵，並按一下選取範圍內的控制項將此控制項主控該選取項目中。 如需詳細資訊，請參閱 <<c0> [ 指定主控項](../windows/specifying-the-dominant-control.md)。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[選取控制項](../windows/selecting-controls.md)  
[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)