---
title: 群組對話方塊上的選項按鈕 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.grouping
dev_langs:
- C++
helpviewer_keywords:
- member variables, adding to radio button groups
- variables, dialog box control member variables
- dialog box controls, grouping radio buttons
- grouping controls
- radio buttons, grouping on dialog boxes
ms.assetid: 3cc43f9e-56c8-4faa-9930-ce81733c69de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c3d0e20d8b2b88a7141672117d4c0b036682953e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641414"
---
# <a name="grouping-radio-buttons-on-a-dialog-box"></a>群組對話方塊上的選項按鈕
當您新增到對話方塊中的選項按鈕時，將它們視為一組藉由設定**群組**中的屬性**屬性**群組中的第一個按鈕的視窗。 然後，這個選項按鈕的控制項識別碼就會出現在 [[加入成員變數精靈]](../ide/add-member-variable-wizard.md)中，讓您為選項按鈕群組加入成員變數。  
  
 對話方塊中可以有多個選項按鈕群組，但加入每個群組時請一定要使用下列程序。  
  
### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>在對話方塊中加入選項按鈕群組  
  
1.  在 [[工具箱] 視窗](/visualstudio/ide/reference/toolbox) 中選取選項按鈕控制項，然後在對話方塊中按一下要放置控制項的位置。  
  
2.  重複步驟 1 加入您需要的數量無限的選項按鈕。 請確定群組中的選項按鈕的定位順序是連續的 (如需詳細資訊，請參閱 [變更控制項的定位順序](../windows/changing-the-tab-order-of-controls.md))。  
  
3.  在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)中，請將定位順序 **第一** 之選項按鈕的 [群組]  屬性設為 **True**。  
  
     將 [群組]  屬性變更成 **True** ，可在資源指令碼之對話方塊物件的按鈕項目中加入 WS_GROUP 樣式，確保使用者在按鈕群組中一次只能選取一個選項按鈕 (當使用者按一下某個選項按鈕時，就會清除群組中的其他按鈕)。  
  
    > [!NOTE]
    >  群組中，應該只有第一個選項按鈕的 [群組]  屬性設為 **True**。 如果有不屬於按鈕群組的其他控制項，請將 **群組之外** 第一個控制項的 [群組]  屬性也設成 **True** 。 按下，您可以快速識別群組之外的第一個控制項**Ctrl**+**D**檢視 索引標籤順序。  
  
### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>加入選項按鈕群組的成員變數  
  
1.  以滑鼠右鍵按一下定位順序第一的選項按鈕控制項 (主控項和 [群組]  屬性設為 True 的控制項)。  
  
2.  從快顯功能表選擇 [加入變數]  。  
  
3.  在 [[加入成員變數精靈]](../ide/add-member-variable-wizard.md)中，選取 [控制項變數]  核取方塊，然後選取 [值]  選項按鈕。  
  
4.  在 [變數名稱]  方塊中，輸入新成員變數的名稱。  
  
5.  在 **變數的型別**清單方塊中，選取**int**或型別`int`。  
  
6.  您現在可以修改程式碼，指定應該顯示為已選取的按鈕。 比方說，`m_radioBox1 = 0;`會選取第一個選項按鈕群組中。  
  
 如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [在對話方塊上的控制項的排列方式](../windows/arrangement-of-controls-on-dialog-boxes.md)   
 [在對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)   
 [控制項](../mfc/controls-mfc.md)