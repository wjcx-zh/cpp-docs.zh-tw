---
title: 裝置影像 （圖示影像編輯器） 中建立透明或反向區域 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cursors [C++], screen regions
- inverse colors, device images
- transparent regions, device images
- transparency, device images
- Image editor [C++], device images
- inverse regions, device images
- cursors [C++], transparent regions
- screen colors
- regions, transparent
- icons [C++], transparent regions
- display devices, transparent and screen regions
- transparent regions in devices
- regions, inverse
- colors [C++], Image editor
- device projects, transparent images
- icons [C++], screen regions
ms.assetid: a994954b-b039-4391-a535-58d1fa10fc3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ba32b0c15f6262763fa001d89d3439c153f5fa3d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680285"
---
# <a name="creating-transparent-or-inverse-regions-in-device-images-image-editor-for-icons"></a>在裝置影像中建立透明或反向區域 (圖示影像編輯器)

在 [影像編輯器](../windows/image-editor-for-icons.md)，初始的圖示或游標影像具有透明屬性。 圖示和游標影像是矩形，雖然許多不會出現，因為影像的部分是透明的;透過圖示或游標會顯示在螢幕上的基礎映像。 當您拖曳圖示時，影像的部分可能會出現反轉的色彩。 您建立這種效果藉由設定螢幕色彩和中的反向色彩[色彩視窗](../windows/colors-window-image-editor-for-icons.md)。

套用至圖示的螢幕及反向色彩和資料指標不是圖形色彩衍生的映像就是指定反向區域。 色彩表示具有那些屬性的映像的組件。 您可以變更，表示在編輯畫面色彩及反向色彩屬性的色彩。 這些變更不會影響您的應用程式中的資料指標之圖示的外觀。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。

### <a name="to-create-transparent-or-inverse-regions"></a>若要建立透明或反向區域

1. 在 [**色彩**] 視窗中，按一下**螢幕色彩**選取器或**反向色彩**選取器。

2. 適用於反向色彩拖曳至您的映像使用繪圖工具的螢幕。 如需有關繪圖工具的詳細資訊，請參閱 <<c0> [ 使用繪圖工具](using-a-drawing-tool-image-editor-for-icons.md)。

### <a name="to-change-the-screen-or-inverse-color"></a>若要變更螢幕或反向色彩

1. 選取 **螢幕色彩**選取器或**反向色彩**選取器。

2. 選擇從色彩**色彩**中的調色盤**色彩**視窗。

   其他選取器時，會自動被指定互補色。

   > [!TIP]
   > 如果您按兩下**螢幕色彩**或**反向色彩**選取器[自訂色彩選取器對話方塊](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)隨即出現。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)  
[圖示和游標： 顯示裝置的影像資源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)