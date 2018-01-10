---
title: "MFC ActiveX 控制項： 加入內建方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2531f84974626fcdb364df67b12f27d61e75a62a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>MFC ActiveX 控制項：加入內建方法
內建方法與自訂方法的類別已實作[COleControl](../mfc/reference/colecontrol-class.md)。 例如，`COleControl`包含預先定義的成員函式，可支援您的控制項重新整理方法。 此內建方法的分派對應項目是**DISP_STOCKFUNC_REFRESH**。  
  
 `COleControl`支援兩個內建的方法： DoClick 和重新整理。 重新整理會叫用控制項的使用者，若要立即更新控制項的外觀。叫用 DoClick 引發控制項的 Click 事件。  
  
|方法|分派對應項目|註解|  
|------------|------------------------|-------------|  
|`DoClick`|**DISP_STOCKPROP_DOCLICK （)**|引發 Click 事件。|  
|**重新整理**|**DISP_STOCKPROP_REFRESH （)**|立即更新控制項的外觀。|  
  
##  <a name="_core_adding_a_stock_method_using_classwizard"></a>新增內建方法，使用加入方法精靈  
 新增內建的方法很簡單使用[加入方法精靈](../ide/add-method-wizard.md)。 下列程序示範如何將重新整理方法新增至使用 MFC ActiveX 控制項精靈所建立的控制項。  
  
#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>若要加入內建的重新整理方法使用加入方法精靈  
  
1.  載入控制項專案。  
  
2.  在 [類別檢視] 中，展開控制項的程式庫節點。  
  
3.  在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。  
  
4.  從捷徑功能表，按一下 **新增**，然後按一下 **加入方法**。  
  
     這會開啟 加入方法精靈。  
  
5.  在**方法名稱**方塊中，按一下**重新整理**。  
  
6.  按一下 [ **完成**]。  
  
##  <a name="_core_classwizard_changes_for_stock_methods"></a>加入方法精靈變更為內建方法  
 因為控制項的基底類別，支援內建的重新整理方法**加入方法精靈**不會變更控制項的類別宣告，以任何方式。 它會加入至控制項的分派對應和方法的項目其。IDL 檔案。 下列這一行加入至控制項的分派對應，它的實作中 (。CPP) 檔案：  
  
 [!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]  
  
 這樣會重新整理方法提供給控制項的使用者。  
  
 下列這一行加入至控制項的。IDL 檔案：  
  
 [!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]  
  
 這一行會重新整理方法指派特定的識別碼。  
  
## <a name="see-also"></a>請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)

