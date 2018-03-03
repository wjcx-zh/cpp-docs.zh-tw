---
title: "建立自訂筆刷 （圖示影像編輯器） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- colors [C++], brush
- brushes, colors
- brushes, creating custom
- images [C++], creating custom brushes
- graphics [C++], custom brushes
- custom brushes
ms.assetid: 750881aa-6f47-4de9-8ca6-a7a12afc6383
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 38f376053635708372c09a37aa0810e4305db60a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-custom-brush-image-editor-for-icons"></a>建立自訂筆刷 (圖示影像編輯器)
自訂筆刷為矩形拾取，並使用類似影像編輯器的備妥的筆刷的映像的一部分。 您可以在選取項目執行的所有作業，您可以都執行以及自訂筆刷。  
  
### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>若要從映像的一部分來建立自訂筆刷  
  
1.  [選取的映像的一部分](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)您想要使用筆刷。  
  
2.  持有**SHIFT**鍵、 按一下 選取範圍中並拖曳影像。  
  
     \-或-  
  
3.  從**映像**功能表上，選擇**將選取範圍當做筆刷**。  
  
     您的選擇會成為自訂筆刷分散映像選取項目中的色彩。 拖曳路徑上也會保留選取項目的複本。 您拖曳的放慢，進行多個複本。  
  
     **請注意**按一下**選取做為筆刷**沒有先選取影像的部分會使用整個映像做為筆刷。 使用自訂筆刷的結果也將取決於您是否選取了[不透明或透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。  
  
 自訂筆刷符合目前的背景色彩的像素通常是透明： 它們不會覆蓋現有的映像。 您可以變更此行為，讓背景色彩的像素繪製在現有的映像。  
  
 您可以使用像是戳記或樣板的自訂筆刷建立各種不同的特殊效果。  
  
#### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>若要以背景色彩繪製自訂筆刷形狀  
  
1.  [選取的不透明或透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。  
  
2.  [設定背景色彩](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)要繪製的色彩。  
  
3.  將您想要繪製自訂筆刷。  
  
4.  按一下滑鼠右鍵。 任何自訂筆刷的不透明區域的背景色彩繪製。  
  
#### <a name="to-double-or-halve-the-custom-brush-size"></a>若要按兩下一半自訂筆刷的大小  
  
1.  按**加號**(**+**) 筆刷的大小增加兩倍索引鍵或**減號**(**-**) 減半的索引鍵.  
  
#### <a name="to-cancel-the-custom-brush"></a>若要取消自訂筆刷  
  
1.  按**ESC**或選擇另一個繪圖工具。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
### <a name="requirements"></a>需求  
 無  
  
## <a name="see-also"></a>請參閱  
 [快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)   
 [編輯圖形資源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [圖示影像編輯器](../windows/image-editor-for-icons.md)

