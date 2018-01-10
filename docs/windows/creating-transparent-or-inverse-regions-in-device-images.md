---
title: "裝置影像 （圖示影像編輯器） 中建立透明或反向區域 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1f416b31200352fc849fb2d1c7a43f9759da47d2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-transparent-or-inverse-regions-in-device-images-image-editor-for-icons"></a>在裝置影像中建立透明或反向區域 (圖示影像編輯器)
在[影像編輯器](../windows/image-editor-for-icons.md)，初始的圖示或游標影像的透明的屬性。 圖示和游標影像是矩形，雖然許多不會出現，因為組件的映像皆為透明的;基礎映像，在螢幕上的顯示的圖示或游標。 當您拖曳圖示時，映像的組件可能會出現反轉的色彩。 設定螢幕色彩和反向色彩中的建立這種效果[色彩視窗](../windows/colors-window-image-editor-for-icons.md)。  
  
 套用至圖示螢幕及反向色彩和資料指標不是圖形色彩衍生的映像就是指定反向區域。 色彩表示具有那些屬性之映像的組件。 您可以變更編輯螢幕色彩及反向色彩屬性的色彩。 這些變更不會影響圖示或游標置於您的應用程式的外觀。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-create-transparent-or-inverse-regions"></a>若要建立透明或反向區域  
  
1.  在**色彩**視窗中，按一下 **螢幕色彩**選取器或**反向色彩**選取器。  
  
2.  適用於反向色彩拖曳至您的映像使用繪圖工具的螢幕。 如需有關繪圖工具的詳細資訊，請參閱[使用繪圖工具](using-a-drawing-tool-image-editor-for-icons.md)。  
  
### <a name="to-change-the-screen-or-inverse-color"></a>若要變更螢幕或反向色彩  
  
1.  選取 **螢幕色彩**選取器或**反向色彩**選取器。  
  
2.  選擇的色彩**色彩**調色盤中的**色彩**視窗。  
  
     其他選取器，會自動指定互補色。  
  
    > [!TIP]
    >  如果您按兩下螢幕色彩或反向色彩選取器[自訂色彩選取器對話方塊](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)隨即出現。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
 需求  
  
 無  
  
## <a name="see-also"></a>請參閱  
 [快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)   
 [圖示和游標： 顯示裝置的影像資源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)

