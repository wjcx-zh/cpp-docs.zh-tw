---
title: 建立的工具提示的工具列按鈕 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tool tips [C++], adding to toolbar buttons
- "\nin tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor [C++], creating tool tips
ms.assetid: 0af65342-fd78-4e78-8d0d-dc68f7fc462e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2d03b71f862e31a2bef25d89c0347c95da240642
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422664"
---
# <a name="creating-a-tool-tip-for-a-toolbar-button-c"></a>工具列按鈕 （c + +） 建立的工具提示

### <a name="to-create-a-tool-tip"></a>若要建立工具提示

1. 選取工具列按鈕。

2. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，請在**提示**屬性欄位中，新增按鈕，[狀態] 列，在訊息之後的描述，並新增`\n`和工具提示名稱。

工具提示的常見範例是**列印**按鈕**WordPad**:

1. 開啟**WordPad**。

2. 將滑鼠指標停留**列印**工具列按鈕。

3. 請注意，這個字`Print`現在浮動在滑鼠指標。

4. 查看 狀態 列 (在最底端**WordPad**  視窗)-請注意現在會顯示文字`Prints the active document`。

`Print`中**步驟 3**是 「 工具提示名稱 」，而`Prints the active document`從**步驟 4** "的描述 [狀態] 列的按鈕。 」

如果您想使用此效果 **工具列**編輯器 」 中，您將**提示**屬性設`Prints the active document\nPrint`。

> [!NOTE]
> 您可以編輯的提示文字使用[屬性 視窗](/visualstudio/ide/reference/properties-window)。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

MFC 或 ATL

## <a name="see-also"></a>另請參閱

[建立、移動和編輯工具列按鈕](../windows/creating-moving-and-editing-toolbar-buttons.md)<br/>
[工具列編輯器](../windows/toolbar-editor.md)