---
title: 建立自訂筆刷 （圖示影像編輯器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- colors [C++], brush
- brushes, colors
- brushes, creating custom
- images [C++], creating custom brushes
- graphics [C++], custom brushes
- custom brushes
ms.assetid: 750881aa-6f47-4de9-8ca6-a7a12afc6383
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bd4a25b208232c8a0923e33156730fc5612219a5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388195"
---
# <a name="creating-a-custom-brush-image-editor-for-icons"></a>建立自訂筆刷 (圖示影像編輯器)

自訂筆刷是您挑選並使用類似的其中一個映像的矩形部分**映像**編者備妥的筆刷。 您可以在 選取項目執行的所有作業，您可以都執行以及自訂筆刷。

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>若要建立自訂筆刷從映像的一部分

1. [選取的映像的一部分](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)您想要使用的筆刷。

2. 持有**Shift**鍵、 按一下 選取範圍中並拖曳影像。

   \-或-

3. 從**映像**功能表上，選擇**將選取範圍當做筆刷**。

   您的選取項目會成為自訂筆刷可將選取範圍中的色彩分散到映像。 選取範圍的複本會保留在拖曳的路徑。 您將拖曳的速度變慢，進行更多的複本。

   > [!NOTE]
   > 按一下 **使用選取範圍當做筆刷**沒有先選取影像的部分會使用整個映像當做筆刷。 使用自訂筆刷的結果也取決於您是否選取了[不透明或透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。

在 自訂筆刷符合目前的背景色彩的像素通常是透明： 它們不會覆蓋現有的映像。 您可以變更此行為，使背景色彩的像素蓋過現有的映像。

您可以使用像是戳記或樣板的自訂筆刷來建立各種不同的特殊效果。

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>若要繪製自訂筆刷形狀中的背景色彩

1. [選取的不透明或透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。

2. [設定背景色彩](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)為您要在其中繪製的色彩。

3. 將自訂的筆刷您要繪製的位置。

4. 按一下滑鼠右鍵。 任何自訂的筆刷的不透明的區域會繪製背景的色彩。

### <a name="to-double-or-halve-the-custom-brush-size"></a>按兩下，或自訂的筆刷的大小則為一半

1. 按下**加號**(**+**) 索引鍵的兩倍筆刷的大小，或有**減號**(**-**) 減半的索引鍵.

### <a name="to-cancel-the-custom-brush"></a>若要取消的自訂筆刷

1. 按下**Esc**或選擇另一個繪圖工具。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[編輯圖形資源](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[圖示影像編輯器](../windows/image-editor-for-icons.md)