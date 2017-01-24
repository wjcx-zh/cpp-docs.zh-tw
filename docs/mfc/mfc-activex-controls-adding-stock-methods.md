---
title: "MFC ActiveX 控制項：加入內建方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DoClick 方法"
  - "MFC ActiveX 控制項, 方法"
  - "MFC ActiveX 控制項, 內建方法"
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項：加入內建方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

內建方法與自訂方法不同之處在於它由 [COleControl](../mfc/reference/colecontrol-class.md)類別已經實作。  例如， `COleControl` 會包含支援您的控制項重新整理方法之預先定義的成員函式。  這個內建方法的分派對應項目是 **DISP\_STOCKFUNC\_REFRESH**。  
  
 `COleControl` 支援兩個內建方法:DoClick 和重新整理。  重新整理控制項的使用者叫用立即更新控制項的外觀;叫用 DoClick 引發控制項的 Click 事件。  
  
|方法|分派對應項目|Comment|  
|--------|------------|-------------|  
|`DoClick`|**DISP\_STOCKPROP\_DOCLICK \(\)**|引發 Click 事件。|  
|**重新整理**|**DISP\_STOCKPROP\_REFRESH \(\)**|立即更新控制項的外觀。|  
  
##  <a name="_core_adding_a_stock_method_using_classwizard"></a> 將使用加入方法精靈的內建方法  
 將內建方法使用 [加入方法精靈](../ide/add-method-wizard.md)很簡單。  下列程序示範如何將方法重新整理到使用 MFC ActiveX 控制項精靈所建立的控制項。  
  
#### 使用加入方法精靈，將這個共用重新整理方法  
  
1.  載入控制項的專案。  
  
2.  在類別檢視中，展開您的控制項程式庫節點。  
  
3.  以滑鼠右鍵按一下控制項的 \(程式庫節點的第二個節點介面節點\) 開啟捷徑功能表。  
  
4.  從捷徑功能表上，按一下 **Add** 然後按一下 **Add Method**。  
  
     這會開啟加入方法精靈。  
  
5.  在 **Method Name** 方塊中，按一下 **Refresh**。  
  
6.  按一下 \[**完成**\]。  
  
##  <a name="_core_classwizard_changes_for_stock_methods"></a> 加入方法內建方法的精靈變更  
 由於這個共用重新整理方法是由控制項的基底類別以任何方式支援， **Add Method Wizard** 不會變更控制項的類別宣告。  它的方法加入項目至控制項的分派對應到和其 .IDL 檔案。  下列程式碼行加入至控制項的分派對應，其實作 \(.CPP\) 檔案:  
  
 [!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-methods_1.cpp)]  
  
 這個重新整理方法提供給控制項的使用者。  
  
 下列程式碼行加入至控制項的 .IDL 檔案:  
  
 [!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-methods_2.idl)]  
  
 這一行會將方法重新整理每個特定 ID 編號。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)