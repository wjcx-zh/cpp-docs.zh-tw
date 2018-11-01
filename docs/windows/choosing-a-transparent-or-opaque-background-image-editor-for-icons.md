---
title: 選擇透明或不透明背景 (圖示影像編輯器)
ms.date: 11/04/2016
helpviewer_keywords:
- opaque backgrounds [C++]
- colors [C++], image
- Image editor [C++], transparent or opague backgrounds
- images [C++], transparency
- images [C++], opaque background
ms.assetid: 61b743d9-c86b-405d-9a81-0806431b4363
ms.openlocfilehash: a7e4d427a6926d48b5115a1b5bb9ba2ca2d8068c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653527"
---
# <a name="choosing-a-transparent-or-opaque-background-image-editor-for-icons"></a>選擇透明或不透明背景 (圖示影像編輯器)

當您移動或複製的選取項目，從映像時，任何像素選取範圍中符合目前的背景色彩的是，根據預設，透明的;它們不會遮住的目標位置中的像素為單位。

您可以從透明背景 （預設值） 的不透明背景，來回切換。 當您使用選項工具 中，**透明背景**並**不透明的背景**選項會出現在**選項**上的選取器**影像編輯器**工具列 （如下所示）。

![背景選項&#45;不透明或透明](../windows/media/vcimageeditoropaqtranspback.gif "vcImageEditorOpaqTranspBack")<br/>
**透明及不透明的選項**上**影像編輯器工具列**

### <a name="to-switch-between-a-transparent-and-opaque-background"></a>若要切換透明及不透明背景

1. 在 **影像編輯器**工具列上，按一下**選項**選取器，然後按一下適當的背景：

   - `Opaque Background (O)`： 選取範圍的所有組件被遮蔽現有的映像。

   - `Transparent Background (T)`： 現有的映像會顯示符合目前的背景色彩選取範圍的組件。

\-或-

- 在 **映像**功能表上，選取或清除**繪製不透明**。

當選取範圍已變更影像的哪些部分而言是透明的作用中時，您可以變更背景色彩。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[使用色彩](../windows/working-with-color-image-editor-for-icons.md)