---
title: 文字工具對話方塊 （c + +） （圖示影像編輯器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.texttool
dev_langs:
- C++
helpviewer_keywords:
- text, adding to an image
- Text Tool dialog box [C++]
ms.assetid: a6036ef4-1871-40db-8239-6ddbe8f422f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e55ad361c9252cfc4989926f90a9fedfd523c7d9
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313440"
---
# <a name="text-tool-dialog-box-c-image-editor-for-icons"></a>文字工具對話方塊 （c + +） （圖示影像編輯器）

使用**文字工具**對話方塊中，將文字加入至資料指標、 點陣圖或圖示的資源。

若要存取此對話方塊中，開啟[影像編輯器](../windows/window-panes-image-editor-for-icons.md)。 選取 **工具**從**映像**功能表，然後再選取**文字工具**命令。

### <a name="font-button"></a>[字型] 按鈕

會開啟[文字工具字型對話方塊](../windows/text-tool-font-dialog-box-image-editor-for-icons.md)，可以變更字型、 樣式或資料指標字型的大小。 變更會套用至中顯示的文字**文字**區域。

### <a name="text-area"></a>文字區域

顯示文字顯示為資源的一部分。 一開始，此區域是空的。

> [!NOTE]
> 如果**透明背景**已經設定，只有文字會放入映像。 如果**不透明背景**已設定的周框，填滿[背景色彩](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)，將會放置文字的背景。 如需詳細資訊，請參閱 <<c0> [ 選擇不透明和透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。

您可以以滑鼠右鍵按一下**文字工具**對話方塊，即可存取預設的捷徑功能表，其中包含一份標準的 Windows 命令。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[編輯圖形資源](../windows/editing-graphical-resources-image-editor-for-icons.md)