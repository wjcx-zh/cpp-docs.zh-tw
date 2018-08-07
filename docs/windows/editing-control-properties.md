---
title: 編輯控制項屬性 |Microsoft Docs
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
ms.openlocfilehash: fa1283f90560390f8fc14ee13d1ab022bbeeff11
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2018
ms.locfileid: "39568858"
---
# <a name="editing-control-properties"></a>編輯控制項屬性
### <a name="to-edit-the-properties-of-a-control-or-controls"></a>若要編輯的控制項或控制項屬性  
  
1.  在對話方塊中，選取您想要修改的控制項。  
  
    > [!NOTE]
    >  如果您選取多個控制項時，就可以編輯只有選取的控制項通用的屬性。  
  
2.  在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，變更您的控制項的屬性。  
  
    > [!NOTE]
    >  當您設定**點陣圖**按鈕、 選項按鈕或等於的核取方塊控制項內容 **，則為 True**，為您的控制項實作 BS_BITMAP 樣式。 如需詳細資訊，請參閱 <<c0> [ 按鈕樣式](../mfc/reference/styles-used-by-mfc.md#button-styles)。 如需範例的關聯控制項的點陣圖，請參閱[CButton::SetBitmap](../mfc/reference/cbutton-class.md#setbitmap)。 當您在對話方塊資源編輯器中，點陣圖不會出現在您的控制項。  
  
### <a name="to-undo-changes-to-the-properties-of-a-control"></a>若要復原變更控制項的屬性  
  
1.  請確定控制項具有焦點，在對話方塊編輯器中。  
  
2.  選擇**恢復**從**編輯**功能表 (如果焦點在控制項上，不是**復原**命令將會無法使用)。  
  
 如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[逐步解說： 當地語系化 Windows Forms](http://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5)並[逐步解說： 使用資源以利用 ASP.NET 進行當地語系化](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。  
  
## <a name="requirements"></a>需求  
  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)