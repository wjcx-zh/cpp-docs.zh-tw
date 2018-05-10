---
title: 變更影像屬性 （圖示影像編輯器） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- images [C++], properties
- Image editor [C++], Properties window
- Image editor [C++], image properties
- Properties window, image editor
ms.assetid: f6172bf1-08c4-4dfd-b542-dd8749e83fe6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 79903e198ddd418b96b0fac2a464dc130d81614e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="changing-image-properties-image-editor-for-icons"></a>變更影像屬性 (圖示影像編輯器)
您可以設定或修改的映像使用內容[屬性 視窗](/visualstudio/ide/reference/properties-window)。  
  
### <a name="to-change-an-images-properties"></a>若要變更影像屬性  
  
1.  開啟中的映像**映像**編輯器。  
  
2.  在**屬性**視窗中，變更您的映像的任何或所有內容。  
  
    |屬性|描述|  
    |--------------|-----------------|  
    |**色彩**|指定影像的色彩配置。 選取色彩的單色，16，或 256，則為 True。 如果您已經有繪製 16 色影像，選取 單色會映像中的黑白色彩的替代項目。 對比永遠不會保留： 例如，相鄰的紅色和綠色的區域都會轉換為黑色。|  
    |**檔案名稱**|指定映像檔的名稱。 根據預設，Visual Studio 指派給基底的檔名，移除前四個字元 ("IDB_") 建立的預設資源識別元 (IDB_BITMAP1) 並加入適當的副檔名。 在此範例中的映像的檔案名稱會是 BITMAP1.bmp。 您無法將它重新命名 MYBITMAP1.bmp。|  
    |**高度**|設定影像的高度 （以像素為單位）。 預設值是 48。 則會裁剪影像，或加入現有影像下方的空白。|  
    |**ID**|設定資源的識別項。 針對映像，Microsoft Visual Studio 中，依預設，會將指派序列中的下一個可用的識別項： IDB_BITMAP1、 IDB_BITMAP2，依此類推。 圖示和游標，會使用類似的名稱。|  
    |**調色盤**|變更色彩屬性。 按兩下，以選取色彩和顯示[自訂色彩選取器對話方塊](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)。 將色彩定義在適當的文字方塊中輸入 RGB 或 HSL 值。|  
    |**SaveCompressed**|指出影像是否以壓縮格式。 這個屬性是唯讀的。 Visual Studio 不允許您將映像儲存在壓縮的格式，以便在 Visual Studio 中建立任何映像，這個屬性將**False**。 如果您在 Visual Studio 中開啟 （建立另一個程式中） 的壓縮映像，這個屬性會是**True**。 如果您儲存使用 Visual Studio 的壓縮映像，將會被解壓縮，這個屬性會回復為**False**。|  
    |**寬度**|設定影像的寬度 （以像素為單位）。 點陣圖的預設值是 48。 則會裁剪影像，或現有的映像的右邊就會加入空格。|  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
 需求  
  
 無  
  
## <a name="see-also"></a>另請參閱  
 [快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)   
 [編輯圖形資源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [圖示影像編輯器](../windows/image-editor-for-icons.md)

