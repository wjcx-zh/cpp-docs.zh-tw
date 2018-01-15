---
title: "圖示和游標： 顯示裝置 （圖示影像編輯器） 的影像資源 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.icon
dev_langs: C++
helpviewer_keywords:
- cursors [C++], creating
- image resources, display devices
- icons [C++], creating
- cursors [C++], types
- icons [C++]
- Image editor [C++], icons and cursors
- cursors [C++]
- display devices, creating icons for
- cursors [C++], hot spots
- icons [C++], types
ms.assetid: 8f0809a8-0cf0-4da9-b23d-51f28bf15f5b
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 99ed2e99c3a08b473dcc786ed47bc088b8fd8a4f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons"></a>圖示和游標：顯示裝置的影像資源 (圖示影像編輯器)
圖示和游標為圖形化資源，可包含不同類型之顯示裝置的多種影像 (不同的大小和色彩配置)。 此外，游標具有「作用點」(hot spot)，Windows 會用它來追蹤游標的位置。 您可以使用影像編輯器來建立及編輯圖示和游標，就像是點陣圖和其他影像一樣。  
  
 當您建立新的圖示或游標時，影像編輯器會先建立一個標準類型的影像， 而且一開始會以螢幕 (透明) 色彩填滿影像。 如果影像是游標，其作用點一開始會在左上角 (座標 0,0)。  
  
 根據預設，影像編輯器可以為下表所示的裝置建立其他影像。 您可以在 [[自訂影像]](custom-image-dialog-box-image-editor-for-icons.md)對話方塊中輸入寬度、高度和色彩計數等參數，為其他裝置建立影像。  
  
> [!NOTE]
>  您可以使用影像編輯器來檢視 32 位元影像，但是無法編輯這類影像。  
  
|色彩|寬度 (像素)|高度 (像素)|  
|-----------|----------------------|-----------------------|  
|單色|16|16|  
|單色|32|32|  
|單色|48|48|  
|單色|64|64|  
|單色|96|96|  
|16|16|16|  
|16|32|32|  
|16|64|64|  
|16|48|48|  
|16|96|96|  
|256|16|16|  
|256|32|32|  
|256|48|48|  
|256|64|64|  
|256|96|96|  
  
-   [建立新的裝置影像 (圖示或游標)](../windows/creating-a-device-image-image-editor-for-icons.md)  
  
-   [加入不同顯示裝置的影像](../windows/adding-an-image-for-a-different-display-device-image-editor-for-icons.md)  
  
-   [複製裝置影像](../windows/copying-a-device-image-image-editor-for-icons.md)  
  
-   [刪除裝置影像](../windows/deleting-a-device-image-image-editor-for-icons.md)  
  
-   [在裝置影像中建立透明或反向區域](../windows/creating-transparent-or-inverse-regions-in-device-images.md)  
  
-   [建立 256 色圖示或游標](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)  
  
-   [設定游標的作用點](../windows/setting-a-cursor-s-hot-spot-image-editor-for-icons.md)  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>需求  
 無  
  
## <a name="see-also"></a>請參閱  
 [圖示影像編輯器](../windows/image-editor-for-icons.md)   
 [圖示](http://msdn.microsoft.com/library/windows/desktop/ms646973)   
 [資料指標](http://msdn.microsoft.com/library/windows/desktop/ms646970)

