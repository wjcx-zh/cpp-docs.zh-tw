---
title: 將點陣圖儲存為 Gif 或 Jpeg （圖示影像編輯器） |Microsoft Docs
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
- .gif files, saving bitmaps as
- jpg files, saving bitmaps as
- jpeg files, saving bitmaps as
- .jpg files, saving bitmaps as
- Image editor [C++], converting image formats
- gif files, saving bitmaps as
- bitmaps [C++], converting formats
- .jpeg files, saving bitmaps as
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 115df69f-10fb-4e6f-906b-853c1e4a54af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: debb2b1e8435cc53ec82ab1f957710850d7b5de3
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010687"
---
# <a name="saving-bitmaps-as-gifs-or-jpegs-image-editor-for-icons"></a>將點陣圖儲存為 GIF 或 JPEG (圖示影像編輯器)
當您建立點陣圖時，格式為點陣圖 (.bmp) 建立映像。 您不過，可以將影像儲存為 GIF 或 JPEG 或其他圖形的格式。  
  
> [!NOTE]
>  此程序不適用於圖示和游標。  
  
### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>若要建立，並將點陣圖儲存為.gif 或.jpeg  
  
1.  從**檔案**功能表上，選擇**開放**，然後按一下**檔案**。  
  
2.  在**新的檔案 對話方塊中**，按一下**Visual c + +** 資料夾，然後選取**點陣圖檔 (.bmp)** 中**範本**方塊，然後按一下**開啟**。  
  
     在中開啟點陣圖**映像**編輯器。  
  
3.  視需要進行變更，新的點陣圖。  
  
4.  與仍在中開啟點陣圖**映像**編輯器中，按一下**儲存*filename*為.bmp**上**檔案**功能表。  
  
5.  在 [**另存新檔**對話方塊方塊中，輸入您想要提供檔案，代表您要的檔案格式的延伸模組的名稱**檔案名稱**] 方塊中。 例如， *myfile.gif*。  
  
     > [!NOTE]
     > 您必須建立或開啟您專案外的點陣圖，以將它儲存為其他檔案格式。 如果您建立或開啟您的專案內**另存新檔**命令將會無法使用。 如需詳細資訊，請參閱 <<c0> [ 檢視資源在資源指令碼檔案外部的專案 （獨立式）](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。  
  
6.  按一下 [儲存] 。  
  
 如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
## <a name="see-also"></a>另請參閱  
 [編輯圖形資源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [圖示影像編輯器](../windows/image-editor-for-icons.md)