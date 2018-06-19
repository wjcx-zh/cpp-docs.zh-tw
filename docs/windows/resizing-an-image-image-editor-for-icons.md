---
title: 調整大小的影像 （圖示影像編輯器） |Microsoft 文件
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
ms.openlocfilehash: c6636e1f92907c301c6e66abd63f744375bffeb8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879044"
---
# <a name="resizing-an-image-image-editor-for-icons"></a>調整影像大小 (圖示影像編輯器)
影像編輯器時調整影像大小的行為取決於您是否曾[選取](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)只是部分或整個影像。  
  
 當選取範圍包含部分影像時，影像編輯器是刪除資料列縮小選取範圍或像素為單位，並填入空白的區域與目前的背景色彩，或它的資料行重複的資料列或資料行的像素為單位延伸選取範圍。  
  
 當選取範圍包含整個影像時，影像編輯器是壓縮和映像，會自動縮放或裁剪並進行擴充。  
  
 有兩種機制來調整影像大小： 調整大小控點和[屬性 視窗](/visualstudio/ide/reference/properties-window)。 您可以拖曳調整大小控點，若要變更所有的大小或影像的一部分。 可讓您拖曳調整大小控點都穩固。 您無法將拖曳空心的控制代碼。 您可以使用 [屬性] 視窗，僅將整個影像調整不選取組件。  
  
 ![調整大小控點，在點陣圖](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")  
縮放控點  
  
> [!NOTE]
>  如果您有中選取的磚方格選項[格線設定對話方塊](../windows/grid-settings-dialog-box-image-editor-for-icons.md)，然後調整 貼齊至下一個圖格格線。 如果只選取 像素格線選項 （預設值），調整大小的下一個可用的像素貼齊。  
  
-   [調整整個影像大小](../windows/resizing-an-entire-image-image-editor-for-icons.md)  
  
-   [裁剪或擴充整個影像](cropping-or-extending-an-entire-image-image-editor-for-icons.md)  
  
-   [縮小或延伸整個影像](../windows/shrinking-or-stretching-an-entire-image-image-editor-for-icons.md)  
  
-   [縮小或延伸影像的一部分](../windows/shrinking-or-stretching-part-of-an-image-image-editor-for-icons.md)  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>需求  
 無  
  
## <a name="see-also"></a>另請參閱  
 [快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)   
 [編輯圖形資源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [圖示影像編輯器](../windows/image-editor-for-icons.md)

