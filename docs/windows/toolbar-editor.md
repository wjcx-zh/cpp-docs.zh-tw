---
title: 工具列編輯器 |Microsoft Docs
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
- resource editors, Toolbar editor
- editors, toolbars
- toolbars [C++], editing
- Toolbar editor
ms.assetid: aa9f0adf-60f6-4f79-ab05-bc330f15ec43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fe9c73a09e2a0f220ee4454baefb07b7e65fcafa
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641643"
---
# <a name="toolbar-editor"></a>工具列編輯器
工具列編輯器可讓您建立工具列資源，並將點陣圖轉換成工具列資源。 工具列編輯器會以圖形方式真實地顯示應用程式完成後的工具列和按鈕。  
  
 使用工具列編輯器可以：  
  
-   [建立新的工具列和按鈕](../windows/creating-new-toolbars.md)  
  
-   [將點陣圖轉換成工具列資源](../windows/converting-bitmaps-to-toolbars.md)  
  
-   [建立、移動和編輯工具列按鈕](../windows/creating-moving-and-editing-toolbar-buttons.md)  
  
-   [建立工具提示](../windows/creating-a-tool-tip-for-a-toolbar-button.md)  
  
 [工具列編輯器] 視窗與 [影像編輯器] 視窗一樣，都會顯示按鈕影像的兩個檢視。 這兩個窗格會以分隔列區隔。 您可隨意地拖曳分隔列，以變更窗格的相對大小。 現用窗格會顯示選取框線。 影像的兩個檢視上方是主旨工具列。  
  
 ![工具列編輯器](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")  
工具列編輯器  
  
 工具列編輯器的功能類似影像編輯器。 其功能表項目、圖形工具和點陣圖格線都與影像編輯器相同。 [影像] 功能表提供一個功能表命令，可讓您在工具列編輯器與影像編輯器之間進行切換。 如需使用圖形工具列、色彩調色盤或 [影像] 功能表的詳細資訊，請參閱 [影像編輯器](../windows/image-editor-for-icons.md)。  
  
 如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>需求  
 MFC 或 ATL  
  
## <a name="see-also"></a>另請參閱  
 [資源編輯器](../windows/resource-editors.md)   
 [功能表和其他資源](http://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)