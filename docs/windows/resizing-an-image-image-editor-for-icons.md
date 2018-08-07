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
ms.openlocfilehash: 41494e8b88f41c4c842e95e9f8a9f5da0247739f
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605639"
---
# <a name="resizing-an-image-image-editor-for-icons"></a>調整影像大小 (圖示影像編輯器)
同時調整影像大小的影像編輯器的行為取決於您是否曾[選取](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)只是部分或整個影像。  
  
 當選取範圍包含只有部分映像時，影像編輯器刪除資料列縮小選取範圍，或藉由複製資料列或資料行的像素的像素為單位，並填入空出的區域，與目前的背景色彩，或它的資料行自動縮放的選取項目。  
  
 當選取範圍包含整個影像時，影像編輯器是壓縮和映像，會自動縮放或裁剪，並將它擴充。  
  
 有兩種機制來調整影像大小： 調整大小控點並[屬性 視窗](/visualstudio/ide/reference/properties-window)。 您可以拖曳調整大小控點，若要變更的所有大小或影像的一部分。 您可以拖曳調整大小控點是純色。 您無法將拖曳空心的控制代碼。 您可以使用 [屬性] 視窗，僅將整個影像調整不會選取的組件。  
  
 ![縮放控點上的點陣圖](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")  
縮放控點  
  
> [!NOTE]
>  如果您有在選取的磚狀格線選項[格線設定對話方塊](../windows/grid-settings-dialog-box-image-editor-for-icons.md)，然後調整大小貼齊至下一個並排顯示格線。 如果只選取 像素格線選項 （預設設定），調整大小貼齊至下一個可用的像素。  
  
-   [調整整個影像大小](../windows/resizing-an-entire-image-image-editor-for-icons.md)  
  
-   [裁剪或擴充整個影像](cropping-or-extending-an-entire-image-image-editor-for-icons.md)  
  
-   [縮小或延伸整個影像](../windows/shrinking-or-stretching-an-entire-image-image-editor-for-icons.md)  
  
-   [縮小或延伸影像的一部分](../windows/shrinking-or-stretching-part-of-an-image-image-editor-for-icons.md)  
  
 如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>需求  
 無  
  
## <a name="see-also"></a>另請參閱  
 [快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)   
 [編輯圖形資源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [圖示影像編輯器](../windows/image-editor-for-icons.md)