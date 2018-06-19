---
title: MFC ActiveX 控制項： 加入自訂方法 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cdf264bd0c2aa44bdeecc58b4bc8eb89c70fb91
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350029"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>MFC ActiveX 控制項：加入自訂方法
自訂的方法與不同的內建方法由不已經實作`COleControl`。 您必須提供每個加入至控制項的自訂方法的實作。  
  
 ActiveX 控制項使用者可以隨時執行特定控制項的動作呼叫的自訂方法。 自訂方法的分派對應項目是表單的`DISP_FUNCTION`。  
  
##  <a name="_core_adding_a_custom_method_with_classwizard"></a> 加入自訂方法具有加入方法精靈  
 下列程序示範如何將 ActiveX 控制項的基本架構程式碼的 PtInCircle 自訂方法。 PtInCircle 決定是否在傳送至控制項的座標之內或之外圓形。 這個相同的程序也可用來加入其他自訂方法。 取代為您自訂的方法名稱和其參數 PtInCircle 方法名稱和參數。  
  
> [!NOTE]
>  這個範例會使用`InCircle`函式，從發行項的事件。 如需此函式的詳細資訊，請參閱文章[MFC ActiveX 控制項： 加入至 ActiveX 控制項的自訂事件](../mfc/mfc-activex-controls-adding-custom-events.md)。  
  
#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>若要加入使用加入方法精靈 PtInCircle 自訂方法  
  
1.  載入控制項的專案。  
  
2.  在 [類別檢視] 中，展開控制項的程式庫節點。  
  
3.  在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。  
  
4.  從捷徑功能表，按一下 **新增**，然後按一下 **加入方法**。  
  
     這會開啟 加入方法精靈。  
  
5.  在**方法名稱**方塊中，輸入`PtInCircle`。  
  
6.  在**內部名稱**方塊中，輸入方法的內部函式的名稱或使用預設值 (在此情況下， `PtInCircle`)。  
  
7.  在**傳回型別**方塊中，按一下**VARIANT_BOOL**方法的傳回型別。  
  
8.  使用**參數型別**和**參數名稱**控制項，加入參數，呼叫`xCoord`(型別**OLE_XPOS_PIXELS**)。  
  
9. 使用**參數型別**和**參數名稱**控制項，加入參數，呼叫`yCoord`(型別**OLE_YPOS_PIXELS**)。  
  
10. 按一下 [ **完成**]。  
  
##  <a name="_core_classwizard_changes_for_custom_methods"></a> 加入方法精靈變更自訂方法  
 當您新增的自訂方法時，加入方法精靈會進行某些變更控制項類別標頭檔 (。H） 和實作 (。CPP) 檔案。 下列這一行加入至控制項類別標頭中的分派對應宣告 (。H） 檔案：  
  
 [!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]  
  
 此程式碼會宣告分派方法的處理常式，呼叫`PtInCircle`。 可以控制使用者使用的外部名稱 PtInCircle 呼叫此函式。  
  
 下列這一行加入至控制項的。IDL 檔案：  
  
 [!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]  
  
 這一行會指派 PtInCircle 方法特定的 ID 編號，加入方法精靈方法和屬性清單中的方法的位置。 加入方法精靈用來加入自訂的方法，因為它的項目已自動加入專案。IDL 檔案。  
  
 此外，下列命令，位於實作 (。Cpp) 的控制項類別中，加入控制項的分派對應：  
  
 [!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]  
  
 `DISP_FUNCTION`巨集對應至控制項的處理常式函式，方法 PtInCircle `PtInCircle`，宣告為傳回型別**VARIANT_BOOL**，並宣告兩個參數的型別**VTS_XPOS_PIXELS**和**VTS_YPOSPIXELS**要傳遞給`PtInCircle`。  
  
 最後，加入方法精靈新增虛設常式函式`CSampleCtrl::PtInCircle`底部的控制項的實作 (。CPP) 檔案。 如`PtInCircle`正常運作，如同先前所述，您必須進行修改，如下所示：  
  
 [!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [類別檢視和物件瀏覽器圖示](/visualstudio/ide/class-view-and-object-browser-icons)

