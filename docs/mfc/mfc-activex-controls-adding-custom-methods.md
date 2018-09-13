---
title: MFC ActiveX 控制項： 加入自訂方法 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
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
ms.openlocfilehash: 3f0d52f3dec2967cc7a8d859e1f6845fe93c6fd6
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45534881"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>MFC ActiveX 控制項：加入自訂方法
自訂方法與不同的內建方法透過未已經實作`COleControl`。 您必須提供每個您新增至您的控制項的自訂方法的實作。

>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需有關取代 ActiveX 的現代技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。  
  
 ActiveX 控制項使用者可以在任何時間執行的特定控制項的動作呼叫的自訂方法。 DISP_FUNCTION 是形式的自訂方法的分派對應項目。  
  
##  <a name="_core_adding_a_custom_method_with_classwizard"></a> 新增自訂方法加入方法精靈  
 下列程序示範如何將 PtInCircle 自訂方法新增至 ActiveX 控制項的基本架構程式碼。 PtInCircle 判斷傳遞給控制項的座標是否內部或外部的圓形。 這個相同的程序也可用來新增其他自訂方法。 替代成您的自訂方法名稱和其 PtInCircle 方法名稱和參數的參數。  
  
> [!NOTE]
>  這個範例會使用`InCircle`函式，從發行項的事件。 如需有關這個函式的詳細資訊，請參閱文章[MFC ActiveX 控制項： 加入至 ActiveX 控制項的自訂事件](../mfc/mfc-activex-controls-adding-custom-events.md)。  
  
#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>若要加入使用加入方法精靈 PtInCircle 自訂方法  
  
1.  載入控制項的專案。  
  
2.  在 [類別檢視] 中，展開控制項的程式庫節點。  
  
3.  在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。  
  
4.  從快顯功能表中，按一下**新增**，然後按一下**加入方法**。  
  
     這會開啟 加入方法精靈。  
  
5.  在 **方法名稱**方塊中，輸入*PtInCircle*。  
  
6.  在 **內部名稱**方塊中，輸入方法的內部函式的名稱或使用預設值 (在此情況下， *PtInCircle*)。  
  
7.  在 **傳回型別**方塊中，按一下**VARIANT_BOOL**方法的傳回型別。  
  
8.  使用**參數的型別**並**參數名稱**控制項，加入名為的參數*xCoord* (型別*OLE_XPOS_PIXELS*)。  
  
9. 使用**參數的型別**並**參數名稱**控制項，加入名為的參數*yCoord* (型別*OLE_YPOS_PIXELS*)。  
  
10. 按一下 [ **完成**]。  
  
##  <a name="_core_classwizard_changes_for_custom_methods"></a> 加入方法精靈變更的自訂方法  
 當您新增的自訂方法時，加入方法精靈會進行一些變更控制項類別的標頭檔 (。H） 和實作 (。CPP) 檔案。 下面這一行新增至分派對應中的宣告，控制類別標頭 (。H） 檔案：  
  
 [!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]  
  
 此程式碼會宣告稱為分派方法處理常式`PtInCircle`。 可以呼叫此函式，控制使用者使用的外部名稱`PtInCircle`。  
  
 下面這一行加入至控制項的。IDL 檔案：  
  
 [!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]  
  
 這一行會將指派`PtInCircle`方法特定的識別碼，加入方法精靈方法和屬性清單中的方法的位置。 加入方法精靈來加入自訂的方法，因為它的項目已自動新增至專案。IDL 檔案。  
  
 此外，下列命令，位於實作 (。控制項類別的 CPP) 檔案會新增至控制項的分派對應：  
  
 [!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]  
  
 DISP_FUNCTION 巨集對應方法`PtInCircle`控制項的處理常式函式，以`PtInCircle`，會宣告為傳回型別**VARIANT_BOOL**，並宣告兩個參數類型**VTS_XPOS_PIXELS**並**VTS_YPOSPIXELS**傳遞給`PtInCircle`。  
  
 最後，加入方法精靈新增虛設常式的函式`CSampleCtrl::PtInCircle`控制項的實作的底部 (。CPP) 檔案。 針對`PtInCircle`運作如先前所述，您必須進行修改，如下所示：  
  
 [!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [類別檢視和物件瀏覽器圖示](/visualstudio/ide/class-view-and-object-browser-icons)

