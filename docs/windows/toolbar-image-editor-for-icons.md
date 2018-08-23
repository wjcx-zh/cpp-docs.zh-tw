---
title: 工具列 （圖示影像編輯器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- Graphics toolbar
- Image editor [C++], toolbar
- Image editor [C++], Option selector
- Properties window
- Option selector, Image editor
ms.assetid: a0af4209-6273-4106-a7c1-0edecc9b5755
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2fbad27020b18bafe2f9fc60ee08282d9101ea5a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604132"
---
# <a name="toolbar-image-editor-for-icons"></a>工具列 (圖示影像編輯器)

**影像編輯器**工具列包含工具，繪圖、 繪圖、 輸入文字、 消除及操作檢視。 它也包含選項選取器，與中，您可以選取使用各項工具的選項。 例如，您可以選擇不同的筆刷寬度、 縮放因素和線條樣式。

> [!NOTE]
> 上提供的所有工具**影像編輯器**工具列也會提供從**映像**功能表 (在**工具**命令)。

![影像編輯器工具列](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar")  
影像編輯器工具列

若要使用**影像編輯器**工具列並**選項**選取器中，按一下工具，或您想要的選項。

> [!TIP]
> 將游標停留在工具列按鈕時，就會出現工具提示。 這些提示可協助您識別每個按鈕的功能。

具有**選項**選取器，您可以指定線條、 筆刷筆劃、 等等的寬度。上的圖示**選項**選取器按鈕變更，視哪一種工具而定，您已選取。

![繪製&#45;影像編輯器工具列上的形狀選取器](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector")  
在 影像編輯器工具列上的選項選取器

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[顯示或隱藏工具列](displaying-or-hiding-the-toolbar-image-editor-for-icons.md)  
[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)  
[圖示影像編輯器](../windows/image-editor-for-icons.md)