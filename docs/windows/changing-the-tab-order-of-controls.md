---
title: 變更控制項的定位順序 |Microsoft Docs
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
- tab controls [C++], tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls [C++], tab order
ms.assetid: e2cee764-4367-42d7-9563-65a68f76f5ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 330fe056a4b06e006d69e630cc933b4402eeb0c0
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316597"
---
# <a name="changing-the-tab-order-of-controls"></a>變更控制項的定位順序

定位順序是順序 **索引標籤**金鑰將輸入的焦點從一個控制項移至 對話方塊中的下一步。 通常是定位順序會繼續從左到右及從上到下一個對話方塊中。 每個控制項都**Tabstop**屬性，可決定控制項是否收到輸入的焦點。

### <a name="to-set-input-focus-for-a-control"></a>若要設定控制項的輸入的焦點

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，選取 **，則為 True**或**False**中**Tabstop**屬性。

即使沒有的控制項**Tabstop**屬性設定為 **，則為 True**必須為定位順序的一部分。 這是很重要，比方說，當您[定義便捷鍵 （助憶鍵）](../windows/defining-mnemonics-access-keys.md)並沒有標題的控制項。 定位順序中，包含相關的控制項的便捷鍵的靜態文字必須緊接著相關的控制項。

> [!NOTE]
> 如果您的對話方塊中包含重疊的控制項，變更索引標籤順序可能會變更控制項的顯示的方式。 定位順序中稍後出現的控制項一律會顯示任何重疊的控制項定位順序中前之上。

### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>若要檢視在對話方塊中的所有控制項目前的定位順序

1. 在 **格式**功能表上，按一下**定位順序**。

\-或-

- 按下**Ctrl**+**D**。

### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>若要變更在對話方塊中的所有控制項的定位順序

1. 在 **格式**功能表上，按一下**定位順序**。

   在左上角的數字，每個控制項目前的定位順序中顯示它的位置。

2. 按一下您想要的順序的每個控制項設定定位順序 **索引標籤**遵循的索引鍵。

3. 按下**Enter**以結束**定位順序**模式。

   > [!TIP]
   > 一旦您輸入**定位順序**模式中，您可以按**Esc**或是**Enter**停用變更定位順序的能力。

### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>若要變更兩個或多個控制項的定位順序

1. 從**格式**功能表上，選擇**定位順序**。

2. 指定順序中的變更將會開始的位置。 若要這樣做，請按住**Ctrl**鍵，然後按一下您想要變更的順序開始之前的控制項。

   比方說，如果您想要變更控制項的順序`7`經由`9`，按住**Ctrl**，然後選取 控制項`6`第一次。

   > [!NOTE]
   > 若要設定特定的控制項數目`1`（先在定位順序），連按兩下控制項。

3. 發行**Ctrl**鍵，然後按一下您想要的順序中的控制項 **索引標籤**遵循從該點的索引鍵。

4. 按下**Enter**以結束**定位順序**模式。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊上控制項的排列方式](../windows/arrangement-of-controls-on-dialog-boxes.md)  
[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)  
[控制項](../mfc/controls-mfc.md)