---
title: MFC ActiveX 控制項：加入自訂方法
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
ms.openlocfilehash: 88d486248eab5d980463764db34bf40b05b830dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364718"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>MFC ActiveX 控制項：加入自訂方法

自定義方法與庫存方法不同,因為它們尚未由`COleControl`實現。 您必須為添加到控制項中的每個自定義方法提供實現。

>[!IMPORTANT]
> ActiveX 是一種不應用於新開發的傳統技術。 有關取代 ActiveX 的現代技術的詳細資訊,請參閱[ActiveX 控制件](activex-controls.md)。

ActiveX 控制件用戶可以隨時呼叫自訂方法以執行特定於控制項的操作。 自定義方法的調度映射條目為窗體DISP_FUNCTION。

## <a name="adding-a-custom-method-with-the-add-method-wizard"></a><a name="_core_adding_a_custom_method_with_classwizard"></a>使用新增方法精靈加入自訂方法

下面的過程演示了將自定義方法 PtInCircle 添加到 ActiveX 控制項的骨架代碼中。 PtInCircle 確定傳遞給控制項的座標是圓內部還是外部。 此過程也可用於添加其他自定義方法。 將自訂方法名稱及其參數替換為 PtInCircle 方法名稱和參數。

> [!NOTE]
> 此範例使用文章事件`InCircle`中的函數。 有關此功能的詳細資訊,請參閱文章[MFC ActiveX 控制件:將自訂事件新增到 ActiveX 控制件](../mfc/mfc-activex-controls-adding-custom-events.md)。

#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>使用新增方法精靈加入 PtInCircle 自訂方法

1. 載入控制項的專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 在快捷選單中,按一下「**添加**」,然後按下「**添加方法**」。

   這將打開"添加方法嚮導」。。

1. 在**方法名稱**框中,鍵入*PtinCircle*。

1. 在 **「內部名稱」** 框中,鍵入方法的內部函數的名稱或使用預設值(本例中為*PtInCircle)。*

1. 在 **「返回類型」** 框中,按一下方法傳回類型的**VARIANT_BOOL。**

1. 使用**參數類型**和**參數名稱**控制項,添加名為*xCoord*的參數 *(OLE_XPOS_PIXELS*類型)。

1. 使用**參數類型**和**參數名稱**控制項,添加名為*yCoord*的參數(類型*OLE_YPOS_PIXELS*)。

1. 按一下 [完成] 。

## <a name="add-method-wizard-changes-for-custom-methods"></a><a name="_core_classwizard_changes_for_custom_methods"></a>為自訂方法加入方法精靈變更

新增自定義方法時,添加方法嚮導會對控制項類標頭 (.H) 和實施 (.CPP)檔。 以下行將添加到控制項類標頭 (中)中的調度映射聲明 (。H) 檔案:

[!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]

此代碼聲明一個稱為`PtInCircle`的調度方法處理程式。 控制項使用者可以使用外部名稱`PtInCircle`調用此功能。

以下行將新增到控制項的 。IDL 檔案:

[!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]

此行為`PtInCircle`方法分配特定的 ID 號、該方法在"添加方法嚮導"方法和屬性清單中的位置。 由於 Add 方法精靈用於新增自訂方法,因此其項目將自動新增到專案的 。IDL 檔。

此外,以下行,位於實現 (。控制類的CPP)檔案,被新增到控制項的調度映射中:

[!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]

DISP_FUNCTION宏`PtInCircle`將該方法映射到控制項的處理程式函數`PtInCircle`, 聲明傳回類型為**VARIANT_BOOL,**`PtInCircle`並聲明要傳遞給的**VTS_XPOS_PIXELS****和VTS_YPOSPIXELS**的兩個參數。

最後,添加方法嚮導將存根函數`CSampleCtrl::PtInCircle`添加到控制項的實現的底部 (。CPP)檔。 要`PtInCircle`按照前面所述運行,必須修改如下:

[!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[類別檢視及物件瀏覽器圖示](/visualstudio/ide/class-view-and-object-browser-icons)
