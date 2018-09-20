---
title: 修改配置格線 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], layout grid
- snap to layout grid
- grids, turning on or off
- layout grid in Dialog Editor
- grids, changing size
ms.assetid: ec31f595-7542-485b-806f-efbaeccc1b3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d583bbbfeb4cd426684d1091a165335f7cbb6e64
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441393"
---
# <a name="modifying-the-layout-grid"></a>修改配置格線

當您要放置或在對話方塊中排列控制項時，您可以使用版面配置方格的更精確的位置。 方格開啟時，控制項便會出現 「 貼齊 」 方格的虛線如同 magnetized。 您可以開啟和關閉此 「 貼齊至格線 」 功能，並變更版面配置方格資料格的大小。

### <a name="to-turn-the-layout-grid-on-or-off"></a>若要開啟或關閉的版面配置方格

1. 從**格式**功能表上，選擇**輔助線設定**。

2. 在 [[輔助線設定對話方塊](../windows/guide-settings-dialog-box.md)，選取或清除**格線**] 按鈕。

   您仍可控制中個別的方格** 對話方塊**使用的編輯器視窗**切換格線**按鈕[對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

### <a name="to-change-the-size-of-the-layout-grid"></a>若要變更版面配置方格的大小

1. 從**格式**功能表上，選擇**輔助線設定**。

2. 在 [輔助線設定對話方塊](../windows/guide-settings-dialog-box.md)，輸入的高度和寬度 Dlu 方格中的資料格。 最小高度或寬度是 4 Dlu。 如需有關 Dlu 的詳細資訊，請參閱[控制項的排列方式 對話方塊上的方式](../windows/arrangement-of-controls-on-dialog-boxes.md)。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊編輯器狀態 (輔助線和格線)](../windows/dialog-editor-states-guides-and-grids.md)<br/>
[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)