---
title: 儲存及載入不同的調色盤 （圖示影像編輯器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.color
dev_langs:
- C++
helpviewer_keywords:
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
ms.assetid: 694b6346-e606-4f19-aa01-9b4ceb47f423
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3ac4a7f23e6f37891851740ed65356d7d2bec3c0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593619"
---
# <a name="saving-and-loading-different-color-palettes-image-editor-for-icons"></a>儲存及載入不同的調色盤 (圖示影像編輯器)

您可以儲存及載入**色彩**包含色板[自訂色彩](../windows/customizing-or-changing-colors-image-editor-for-icons.md)。 (根據預設，**色彩**啟動 Visual Studio 時，會自動載入最近使用的調色盤。)

> [!TIP]
> 由於**映像**編輯器沒有任何方法來還原預設**色彩**調色盤，您應該儲存預設**色彩**調色盤的名稱，例如*以 standard.pal*或是*default.pal*以便您可以輕易地還原預設設定。

### <a name="to-save-a-custom-colors-palette"></a>若要儲存自訂色彩調色盤

1. 從**映像**功能表上，選擇**儲存調色盤**。

2. 瀏覽至您要儲存調色盤的目錄，然後輸入調色盤的名稱。

3. 按一下 [儲存] 。

### <a name="to-load-a-custom-colors-palette"></a>若要載入自訂色彩調色盤

1. 從**映像**功能表上，選擇**載入調色盤**。

2. 在 [載入色彩調色盤對話方塊](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md)、 瀏覽至正確的目錄，然後選取您想要載入的調色盤。 **色彩**調色盤會以.pal 副檔名儲存。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)  
[使用色彩](../windows/working-with-color-image-editor-for-icons.md)