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
ms.openlocfilehash: 14cad19c53e8cd741bf16bab49420169e93f6af6
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606968"
---
# <a name="saving-and-loading-different-color-palettes-image-editor-for-icons"></a>儲存及載入不同的調色盤 (圖示影像編輯器)
您可以儲存及載入色彩調色盤，其中包含[自訂色彩](../windows/customizing-or-changing-colors-image-editor-for-icons.md)。 (根據預設，啟動 Visual Studio 時，會自動載入最近使用的色彩調色盤。)  
  
> [!TIP]
>  由於影像編輯器沒有任何方法來還原預設色彩調色盤，您應該以 standard.pal 或 default.pal 這類名稱儲存預設色彩調色盤，好讓您可以輕鬆地還原預設設定。  
  
### <a name="to-save-a-custom-colors-palette"></a>若要儲存自訂色彩調色盤  
  
1.  從**映像**功能表上，選擇**儲存調色盤**。  
  
2.  瀏覽至您要儲存調色盤的目錄，然後輸入調色盤的名稱。  
  
3.  按一下 [儲存] 。  
  
### <a name="to-load-a-custom-colors-palette"></a>若要載入自訂色彩調色盤  
  
1.  從**映像**功能表上，選擇**載入調色盤**。  
  
2.  在 [載入色彩調色盤對話方塊](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md)、 瀏覽至正確的目錄，然後選取您想要載入的調色盤。 即會以 .pal 副檔名儲存色彩調色盤。  
  
## <a name="requirements"></a>需求  
  
 無  
  
## <a name="see-also"></a>另請參閱  
 [快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)   
 [使用色彩](../windows/working-with-color-image-editor-for-icons.md)