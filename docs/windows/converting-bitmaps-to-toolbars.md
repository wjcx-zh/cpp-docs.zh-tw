---
title: "轉換點陣圖為工具列 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- bitmaps [C++], converting to toolbars
- Toolbar editor, converting bitmaps
- toolbars [C++], converting bitmaps
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 43eda0c6bd875b9fd82ee97d346e3f5d89584795
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="converting-bitmaps-to-toolbars"></a>轉換點陣圖為工具列
轉換點陣圖，您可以建立新的工具列。 將點陣圖圖形將轉換成工具列按鈕影像。 通常，點陣圖包含數個按鈕的影像在單一的點陣圖，每個按鈕的一個映像。 映像可以是任何規模。預設為 16 個像素寬和影像的高度。 您可以指定按鈕中的映像大小[新增工具列資源對話方塊](../windows/new-toolbar-resource-dialog-box.md)當您選擇從工具列編輯器**映像**影像編輯器中的功能表。  
  
### <a name="to-convert-bitmaps-to-a-toolbar"></a>若要將點陣圖轉換成工具列  
  
1.  開啟現有的點陣圖資源中[影像編輯器](../windows/image-editor-for-icons.md)。 (如果點陣圖已不在您的.rc 檔，以滑鼠右鍵按一下.rc 檔，請選擇**匯入**從快顯功能表中，瀏覽至您想要加入至您的.rc 檔，點陣圖，然後按一下 **開啟**。)  
  
2.  從**映像**功能表上，選擇**工具列編輯器**。  
  
     [新增工具列資源對話方塊](../windows/new-toolbar-resource-dialog-box.md)隨即出現。 您可以變更圖示影像以符合點陣圖的高度與寬度。 工具列影像即會顯示在工具列編輯器中。  
  
3.  若要完成轉換，將變更命令**識別碼**按鈕使用[屬性 視窗](/visualstudio/ide/reference/properties-window)。 輸入新**識別碼**或選取**識別碼**從下拉式清單。  
  
    > [!TIP]
    >  [屬性] 視窗包含圖釘按鈕標題列中。 按一下此按鈕啟用或停用自動隱藏視窗。 若要快速瀏覽所有工具列按鈕屬性而不必重新開啟個別的屬性視窗，關閉自動隱藏讓 [屬性] 視窗保持不動。  
  
 您可以使用變更的新工具列上的按鈕命令 Id[屬性 視窗](/visualstudio/ide/reference/properties-window)。 編輯新的工具列上的資訊，請參閱[建立、 移動和編輯工具列按鈕](../windows/creating-moving-and-editing-toolbar-buttons.md)。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](https://msdn.microsoft.com/library/f45fce5x.aspx)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](https://msdn.microsoft.com/library/xbx3z216.aspx)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](https://msdn.microsoft.com/library/h6270d0z.aspx)。  
  
 需求  
  
 MFC 或 ATL  
  
## <a name="see-also"></a>另請參閱  
 [建立新的工具列](../windows/creating-new-toolbars.md)   
 [工具列編輯器](../windows/toolbar-editor.md)

