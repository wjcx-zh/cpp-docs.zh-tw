---
title: 工具列編輯器 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.toolbar.F1
dev_langs:
- C++
helpviewer_keywords:
- resource editors [C++], Toolbar editor
- editors, toolbars
- toolbars [C++], editing
- Toolbar editor
ms.assetid: aa9f0adf-60f6-4f79-ab05-bc330f15ec43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c51c8a5dc321d61b6167fb6a1e5b71d52145d81d
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316948"
---
# <a name="toolbar-editor-c"></a>工具列編輯器 （c + +）

**工具列**編輯器可讓您建立 c + + 工具列資源，並將點陣圖轉換成工具列資源。 **工具列**編輯器来顯示的工具列和按鈕，非常類似於中完成的應用程式外觀將使用的圖形化顯示。

具有**工具列**編輯器，您可以：

- [建立新的工具列和按鈕](../windows/creating-new-toolbars.md)

- [將點陣圖轉換成工具列資源](../windows/converting-bitmaps-to-toolbars.md)

- [建立、移動和編輯工具列按鈕](../windows/creating-moving-and-editing-toolbar-buttons.md)

- [建立工具提示](../windows/creating-a-tool-tip-for-a-toolbar-button.md)

**工具列**編輯器 視窗會顯示兩個按鈕的影像，影像編輯器 視窗相同檢視。 這兩個窗格會以分隔列區隔。 您可隨意地拖曳分隔列，以變更窗格的相對大小。 現用窗格會顯示選取框線。 影像的兩個檢視上方是主旨工具列。

![工具列編輯器](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")  
工具列編輯器

** 工具列**編輯器是類似**映像**編輯器的功能。 功能表項目、 圖形工具和點陣圖格線都與相同**映像**編輯器。 在沒有功能表命令**映像**功能表可讓您切換**工具列**編輯器與**映像**編輯器。 如需有關使用**圖形**工具列**色彩**調色盤，或**映像**功能表上，請參閱[影像編輯器](../windows/image-editor-for-icons.md)。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

MFC 或 ATL

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)  
[功能表和其他資源](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)