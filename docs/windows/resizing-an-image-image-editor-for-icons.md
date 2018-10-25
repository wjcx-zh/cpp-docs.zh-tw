---
title: 調整大小的影像 （圖示影像編輯器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.editing
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dc70d6cd5933608067a43cdb7dcca1e11dd22a2d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50082285"
---
# <a name="resizing-an-image-image-editor-for-icons"></a>調整影像大小 (圖示影像編輯器)

行為**映像**編輯器時調整影像大小取決於您是否曾[選](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)只是部分或整個影像。

選取範圍包含只有部分映像，當**映像**編輯器會藉由刪除資料列或資料行的像素為單位，並以目前的背景色彩填滿空出的區域來縮小選取範圍，或它延伸選取範圍複製的資料列或資料行的像素為單位。

當選取範圍包含整個映像**映像**編輯器是壓縮和映像，會自動縮放或裁剪，並將它擴充。

有兩種機制來調整影像大小： 調整大小控點並[屬性 視窗](/visualstudio/ide/reference/properties-window)。 您可以拖曳調整大小控點，若要變更的所有大小或影像的一部分。 您可以拖曳調整大小控點是純色。 您無法將拖曳空心的控制代碼。 您可以使用**屬性**視窗重新調整整個影像，未選取的組件。

![縮放控點上的點陣圖](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
縮放控點

> [!NOTE]
> 如果您有**圖格的格線**中選取選項[格線設定對話方塊](../windows/grid-settings-dialog-box-image-editor-for-icons.md)，然後調整大小貼齊至下一個並排顯示格線。 如果只有**像素格線**選項是選取 （預設值），調整大小貼齊至下一個可用的像素。

- [調整整個影像大小](../windows/resizing-an-entire-image-image-editor-for-icons.md)

- [裁剪或擴充整個影像](cropping-or-extending-an-entire-image-image-editor-for-icons.md)

- [縮小或延伸整個影像](../windows/shrinking-or-stretching-an-entire-image-image-editor-for-icons.md)

- [縮小或延伸影像的一部分](../windows/shrinking-or-stretching-part-of-an-image-image-editor-for-icons.md)

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[編輯圖形資源](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[圖示影像編輯器](../windows/image-editor-for-icons.md)