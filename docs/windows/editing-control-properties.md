---
title: 編輯控制項屬性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], undoing changes
- controls [C++], editing properties
- dialog box controls, editing properties
ms.assetid: 9bdae21d-6dec-4344-a197-2ca4fc46d040
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f7976f74e9454b023c4da51168fa780ccaea2342
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873481"
---
# <a name="editing-control-properties"></a>編輯控制項屬性
### <a name="to-edit-the-properties-of-a-control-or-controls"></a>若要編輯的控制項屬性  
  
1.  在對話方塊中，選取您想要修改的控制項。  
  
    > [!NOTE]
    >  如果您選取多個控制項，就可以編輯只有選取的控制項通用的屬性。  
  
2.  在[屬性 視窗](/visualstudio/ide/reference/properties-window)，變更控制項的屬性。  
  
    > [!NOTE]
    >  當您將**點陣圖**按鈕、 選項按鈕或核取方塊控制項等於內容**True**，BS_BITMAP 實作控制項的樣式。 如需詳細資訊，請參閱[按鈕樣式](../mfc/reference/styles-used-by-mfc.md#button-styles)。 如需與控制項產生關聯的點陣圖的範例，請參閱[CButton::SetBitmap](../mfc/reference/cbutton-class.md#setbitmap)。 在對話方塊資源編輯器中，點陣圖不會出現在您的控制項。  
  
### <a name="to-undo-changes-to-the-properties-of-a-control"></a>若要復原變更控制項的屬性  
  
1.  請確定焦點在控制項在對話方塊編輯器中。  
  
2.  選擇**復原**從**編輯**功能表 (如果焦點在控制項上不是**復原**命令將會無法使用)。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。* 。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱 [逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) 和 [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。  
  
 需求  
  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)

