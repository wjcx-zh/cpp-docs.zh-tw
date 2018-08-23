---
title: 使用 256 色調色盤 （圖示影像編輯器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- 256-color palette
- colors, icons and cursors
- cursors, color
- color palettes, 256-color
- palettes, 256-color
- icons, color
ms.assetid: 1506ed00-669b-4a21-b1a4-39b6a84a78bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c148fbfe1ba54aab1ccf4ba86c23656ef83e129a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42581017"
---
# <a name="using-the-256-color-palette-image-editor-for-icons"></a>使用 256 色調色盤 (圖示影像編輯器)

若要繪製選取 256 色調色盤中，您必須選取色彩**色彩**中的調色盤[色彩視窗](../windows/colors-window-image-editor-for-icons.md)。

### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>若要從大圖示的 256 色調色盤選擇色彩

1. 選取 大圖示或游標，或建立新的大圖示或游標。

2. 從顯示中的 256 色彩選擇色彩**色彩**中的調色盤**色彩**視窗。

   選取的色彩會變成目前的色彩**色彩**中的調色盤**色彩**視窗。

   > [!NOTE]
   > 256 色的映像所使用的初始調色盤比對所傳回的調色盤`CreateHalftonePalette`Windows API。 適用於 Windows shell 的所有圖示應該都使用這個調色盤來防止重繪閃動期間調色盤實現。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)  
[建立 256 色圖示或游標](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)  
[圖示和游標： 顯示裝置的影像資源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)