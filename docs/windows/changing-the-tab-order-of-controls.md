---
title: 變更控制項的定位順序 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], tab order
- focus, tab order
- tab controls, tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls, tab order
ms.assetid: e2cee764-4367-42d7-9563-65a68f76f5ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 33e6e9624e7e927860a184361d45f855f3a1e4f6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="changing-the-tab-order-of-controls"></a>變更控制項的定位順序
定位順序是以 TAB 鍵輸入的焦點從某個控制項移動到下一個的對話方塊內的順序。 通常從左到右，從上到下對話方塊中，就會繼續在定位順序。 每個控制項都**Tabstop**屬性，可決定控制項是否會收到輸入的焦點。  
  
### <a name="to-set-input-focus-for-a-control"></a>若要設定控制項的輸入的焦點  
  
1.  在[屬性 視窗](/visualstudio/ide/reference/properties-window)，選取**True**或**False**中**Tabstop**屬性。  
  
 即使控制項沒有 Tabstop 屬性設定為定位順序的一部分，則為 True 的需要。 這是很重要，例如，當您[定義便捷鍵 （助憶鍵）](../windows/defining-mnemonics-access-keys.md)沒有標題的控制項。 定位順序中，包含相關控制項的便捷鍵的靜態文字必須緊接著相關的控制項。  
  
> [!NOTE]
>  如果您的對話方塊包含重疊的控制項，變更定位順序可能會變更控制項的顯示的方式。 控制項定位順序中稍後一定會顯示任何重疊的控制項定位順序中之前之上。  
  
#### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>若要在對話方塊中檢視所有控制項的目前索引標籤順序  
  
1.  在**格式**功能表上，按一下 **定位順序**。  
  
 \-或-  
  
-   按下 CTRL + D  
  
#### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>若要變更的對話方塊中的所有控制項的定位順序  
  
1.  在**格式**功能表上，按一下 **定位順序**。  
  
     每個控制項的左上角之數字會顯示目前的定位順序中其所在位置。  
  
2.  按一下您想要遵循的 TAB 鍵順序中的每個控制項設定定位順序。  
  
3.  按**ENTER**結束**定位順序**模式。  
  
    > [!TIP]
    >  一旦您輸入 tab 鍵順序模式，您可以按 esc 鍵或 enter 鍵，若要停用變更定位順序的能力。  
  
#### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>若要變更兩個或多個控制項的定位順序  
  
1.  從**格式**功能表上，選擇**定位順序**。  
  
2.  指定順序中的變更開始的位置。 若要這樣做，請按住**CTRL**鍵，然後按一下您想要變更的順序開始之前的控制項。  
  
     例如，如果您想要變更控制項 7 到 9 的順序，按住 ctrl 鍵，然後先選取控制項 6。  
  
    > [!NOTE]
    >  若要設定特定的控制項 （先在定位順序） 的數字 1，在控制項上按兩下。  
  
3.  釋放 CTRL 鍵，，然後按一下您要從該點遵循 TAB 鍵的順序中的控制項。  
  
4.  按**ENTER**結束**定位順序**模式。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
### <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [在對話方塊上的控制項的排列方式](../windows/arrangement-of-controls-on-dialog-boxes.md)   
 [在對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)   
 [控制項](../mfc/controls-mfc.md)

