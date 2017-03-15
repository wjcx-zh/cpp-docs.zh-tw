---
title: "MFC ActiveX 控制項：加入自訂方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC ActiveX 控制項, 方法"
  - "PtInCircle 自訂方法"
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# MFC ActiveX 控制項：加入自訂方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

自訂方法與內建方法不同尚未由 `COleControl` 實作。  您必須提供每個自訂方法的實作您加入至控制項。  
  
 ActiveX 控制項使用者可以隨時呼叫自訂方法所執行的特定動作。  自訂方法的分派對應項目的格式為 `DISP_FUNCTION`。  
  
##  <a name="_core_adding_a_custom_method_with_classwizard"></a> 將具有的加入方法精靈的自訂方法  
 下列程序示範如何將自訂方法 PtInCircle 到 ActiveX 控制項的最基本的程式碼。  PtInCircle 判斷座標傳遞至控制項內部或在圓形之外。  這個程序也可以用來加入其他自訂方法。  用 PtInCircle 方法名稱和參數替代自訂方法名稱和其參數。  
  
> [!NOTE]
>  這個範例會使用文件事件的 `InCircle` 函式。  如需這個函式的詳細資訊，請參閱本文件的 [MFC ActiveX 控制項:將自訂事件加入 ActiveX 控制項](../mfc/mfc-activex-controls-adding-custom-events.md)。  
  
#### 使用加入方法精靈，將 PtInCircle 自訂方法  
  
1.  載入控制項的專案。  
  
2.  在類別檢視中，展開您的控制項程式庫節點。  
  
3.  以滑鼠右鍵按一下控制項的 \(程式庫節點的第二個節點介面節點\) 開啟捷徑功能表。  
  
4.  在捷徑功能表中，按一下 **加入** 後再按一下加入方法。  
  
     這會開啟加入方法精靈。  
  
5.  在 **方法名稱** 方塊中，輸入 `PtInCircle`。  
  
6.  在 **Internal Name** 方塊中，輸入方法的內部功能的名稱或使用預設值 \(在這種情況下， `PtInCircle`\)。  
  
7.  在 **Return Type** 方塊中，按一下方法之傳回型別的 **VARIANT\_BOOL** 。  
  
8.  使用 **Parameter Type** 和 **Parameter Name** 控制項，加入名為 `xCoord` 的參數型別 \( **OLE\_XPOS\_PIXELS**\)。  
  
9. 使用 **Parameter Type** 和 **Parameter Name** 控制項，加入名為 `yCoord`  的參數型別 \( **OLE\_XPOS\_PIXELS**\)。  
  
10. 按一下 \[**完成**\]。  
  
##  <a name="_core_classwizard_changes_for_custom_methods"></a> 加入方法的自訂方法的精靈變更  
 當您將自訂方法時，加入方法精靈會對控制項類別標頭的變更 \(.H\) 和實作 \(.CPP\) 檔案。  下列程式碼行加入至控制項類別標頭的分派對應宣告 \(.H\) 檔案:  
  
 [!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-methods_1.h)]  
  
 這個程式碼會宣告分派方法會呼叫處理常式的 `PtInCircle`。  這個函式可以使用外部名稱 PtInCircle 的使用者控制項呼叫。  
  
 下列程式碼行加入至控制項的.IDL 檔案:  
  
 [!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-methods_2.idl)]  
  
 這一行會將 PtInCircle 方法每個特定 ID 編號、方法的位置加入方法精靈方法和屬性清單中。  由於加入方法精靈用來加入自訂方法，其項目將會自動加入至專案的 .IDL 檔案。  
  
 此外，下列程式碼行，位於控制項類別的實作 \(.CPP\) 檔案中，加入控制項的分派對應:  
  
 [!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-methods_3.cpp)]  
  
 `DISP_FUNCTION` 巨集對應方法 PtInCircle 對控制項的處理常式函式，則為 `PtInCircle`，宣告傳回型別是 **VARIANT\_BOOL**，並宣告型別傳遞的 **VTS\_XPOS\_PIXELS** 和 **VTS\_YPOSPIXELS** 兩個參數設定為 `PtInCircle`。  
  
 最後，加入方法精靈將 Stub 函式 `CSampleCtrl::PtInCircle` 到控制項的實作 \(.CPP\) 檔案的底部。  如需 `PtInCircle` 函式如先前陳述式，必須修改如下:  
  
 [!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-methods_4.cpp)]  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [類別檢視和物件瀏覽器圖示](../Topic/Class%20View%20and%20Object%20Browser%20Icons.md)