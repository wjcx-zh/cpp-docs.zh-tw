---
title: MFC ActiveX 控制項： 加入內建方法 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 604a095ab26abf4953d56786e00461cabd07e579
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45534946"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>MFC ActiveX 控制項：加入內建方法
內建的方法不同的自訂方法，因為它已經由類別實作[COleControl](../mfc/reference/colecontrol-class.md)。 比方說，`COleControl`包含預先定義的成員函式，為您的控制項支援重新整理方法。 分派對應項目，這個內建的方法是 DISP_STOCKFUNC_REFRESH。

>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需有關取代 ActiveX 的現代技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。  
  
 `COleControl` 支援兩個內建的方法： DoClick 和重新整理。 若要立即更新控制項的外觀，控制項的使用者叫用重新整理叫用 DoClick 引發控制項的 Click 事件。  
  
|方法|分派對應項目|註解|  
|------------|------------------------|-------------|  
|`DoClick`|**DISP_STOCKPROP_DOCLICK （)**|就會引發 Click 事件。|  
|`Refresh`|**DISP_STOCKPROP_REFRESH （)**|立即更新控制項的外觀。|  
  
##  <a name="_core_adding_a_stock_method_using_classwizard"></a> 新增內建方法，使用加入方法精靈  
 新增內建的方法很簡單使用[加入方法精靈](../ide/add-method-wizard.md)。 下列程序示範如何將重新整理方法新增至使用 MFC ActiveX 控制項精靈所建立的控制項。  
  
#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>若要加入內建的重新整理方法使用加入方法精靈  
  
1.  載入控制項專案。  
  
2.  在 [類別檢視] 中，展開控制項的程式庫節點。  
  
3.  在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。  
  
4.  從快顯功能表中，按一下**新增**，然後按一下**加入方法**。  
  
     這會開啟 加入方法精靈。  
  
5.  在 **方法名稱**方塊中，按一下**重新整理**。  
  
6.  按一下 [ **完成**]。  
  
##  <a name="_core_classwizard_changes_for_stock_methods"></a> 加入方法精靈針對變更內建方法  
 因為控制項的基底類別，支援內建的重新整理方法**加入方法精靈**不會變更控制項的類別宣告，以任何方式。 它會將新增的項目，方法為控制項的分派對應，而其。IDL 檔案。 下面這一行加入至控制項的分派對應，位於其實作 (。CPP) 檔案：  
  
 [!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]  
  
 這會重新整理方法提供給控制項的使用者。  
  
 下面這一行加入至控制項的。IDL 檔案：  
  
 [!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]  
  
 這一行會重新整理方法指派特定的識別碼。  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)

