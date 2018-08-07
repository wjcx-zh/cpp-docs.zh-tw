---
title: 調整整個影像 （圖示影像編輯器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], resizing images
- size [C++], images
- images [C++], resizing
- resizing images
ms.assetid: 10782937-7eb4-4340-bdec-618ee7d7904b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f9104feac603819b9420d315e619182722c87474
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606214"
---
# <a name="resizing-an-entire-image-image-editor-for-icons"></a>調整整個影像大小 (圖示影像編輯器)
### <a name="to-resize-an-entire-image-using-the-properties-window"></a>若要調整整個影像使用 [屬性] 視窗的大小  
  
1.  開啟您想要變更其屬性的影像。  
  
2.  在**寬度**並**高度**方塊[屬性 視窗](/visualstudio/ide/reference/properties-window)，輸入您想要的尺寸。  
  
     如果您要增加影像的大小，影像編輯器擴充到右方時，向下、 影像或兩者，並使用目前的背景色彩填滿新的區域。 映像不會自動縮放。  
  
     如果您要縮小映像的大小，影像編輯器會裁剪影像右邊或下邊緣，或兩者。  
  
    > [!NOTE]
    >  您可以使用 Width 和 Height 屬性，只將整個影像，不必調整部分的選取範圍的大小調整。  
  
 如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>需求  
  
 無  
  
## <a name="see-also"></a>另請參閱  
 [快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)   
 [調整影像大小](../windows/resizing-an-image-image-editor-for-icons.md)