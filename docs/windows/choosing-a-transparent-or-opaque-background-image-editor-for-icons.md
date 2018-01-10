---
title: "選擇透明或不透明背景 （圖示影像編輯器） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- opaque backgrounds
- background colors, images
- colors [C++], image
- Image editor [C++], transparent or opague backgrounds
- background images
- images [C++], transparency
- images [C++], opaque background
- transparent backgrounds
- transparency, background
- transparent backgrounds, images
ms.assetid: 61b743d9-c86b-405d-9a81-0806431b4363
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4e73ac7122b31ab6880d7d27387937113dee70f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="choosing-a-transparent-or-opaque-background-image-editor-for-icons"></a>選擇透明或不透明背景 (圖示影像編輯器)
當您移動或複製選取範圍，從映像時，任何像素選取範圍中符合目前的背景色彩是，根據預設，透明的;它們不會遮住目標位置中的像素為單位。  
  
 您可以從透明背景 （預設值） 以透明的背景，來回切換。 當您使用選項工具 中，**透明背景**和**不透明背景**選項出現在 選項 選取器上**影像編輯器**工具列 （如下所示）。  
  
 ![背景選項 &#45;不透明或透明](../windows/media/vcimageeditoropaqtranspback.gif "vcImageEditorOpaqTranspBack")  
透明和不透明影像編輯器工具列上的選項  
  
### <a name="to-switch-between-a-transparent-and-opaque-background"></a>若要切換透明和不透明背景  
  
1.  在**影像編輯器**工具列上，按一下 **選項**選取器，然後按一下適當的背景：  
  
    -   **不透明背景 (O)**： 現有的映像會隱藏選取範圍的所有部分。  
  
    -   **透明背景 (T)**： 現有的影像顯示的選取項目符合目前的背景色彩的組件。  
  
 \-或-  
  
-   在**映像**功能表上，選取或清除**繪製不透明**。  
  
 選取範圍已變更影像的哪些部分皆為透明的作用中時，您可以變更背景色彩。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
 需求  
  
 無  
  
## <a name="see-also"></a>請參閱  
 [快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)   
 [使用色彩](../windows/working-with-color-image-editor-for-icons.md)