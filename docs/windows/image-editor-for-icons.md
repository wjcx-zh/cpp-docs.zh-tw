---
title: 圖示影像編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.cursor.F1
- vc.editors.icon.F1
- vc.editors.cursor
- vc.editors.bitmap.F1
dev_langs:
- C++
helpviewer_keywords:
- editors, images
- resource editors, graphics
- Image editor [C++]
- resource editors, Image editor
ms.assetid: 586d2b8b-0348-4883-a85d-1ff0ddbf14dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 63ab877506c0b38563868374312c8f63bc28333e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583528"
---
# <a name="image-editor-for-icons"></a>圖示影像編輯器

影像編輯器具有用於建立及編輯影像的多功能工具組，以及可協助您建立工具列點陣圖的功能。 除了點陣圖、圖示和游標之外，您還可使用 [ **影像** ] 功能表上的命令和 [ **影像編輯器** ] 工具列上的工具編輯 GIF 或 JPEG 格式的影像。

使用影像編輯器可以：

- [編輯圖形化資源](../windows/editing-graphical-resources-image-editor-for-icons.md)

- [使用色彩](../windows/working-with-color-image-editor-for-icons.md)

- [使用圖示和游標：顯示裝置的影像資源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)

- [使用影像編輯器命令的快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)

**影像編輯器**視窗會顯示兩個映像，以分隔列分隔的兩個窗格檢視。 您可隨意地拖曳分隔列，以變更窗格的相對大小。 現用窗格會顯示選取框線。

**影像編輯器**視窗可以調整以符合您的需求和喜好設定。 您可 [變更放大係數](../windows/changing-the-magnification-factor-image-editor-for-icons.md) 和 [顯示或隱藏像素格線](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md)。

> [!NOTE]
> 使用**影像編輯器**，您可以檢視 32 位元映像，但無法加以編輯。

## <a name="visual-studio-image-library"></a>Visual Studio 影像庫

您可以免費下載**Visual Studio 影像庫**其中包含許多動畫、 點陣圖和圖示，您可以使用您的應用程式中。 如需如何下載程式庫的詳細資訊，請參閱 [Visual Studio 影像程式庫](/visualstudio/designers/the-visual-studio-image-library)。

## <a name="managed-resources"></a>Managed 資源

您可以使用**映像**編輯器並[二進位編輯器](binary-editor.md)來處理 managed 專案中的資源檔。 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)  
[圖示](http://msdn.microsoft.com/library/windows/desktop/ms646973.aspx)