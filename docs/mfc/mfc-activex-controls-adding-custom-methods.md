---
title: MFC ActiveX 控制項：加入自訂方法
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
ms.openlocfilehash: e32a1c372d89fc4ade414b20a0f77fa162807250
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626151"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>MFC ActiveX 控制項：加入自訂方法

自訂方法與內建方法不同之處在于，它們尚未由所執行 `COleControl` 。 您必須為您新增至控制項的每個自訂方法提供執行。

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需取代 ActiveX 之新式技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

ActiveX 控制項使用者可以隨時呼叫自訂方法來執行控制項特定的動作。 自訂方法的分派對應專案的格式為 DISP_FUNCTION。

## <a name="adding-a-custom-method-with-the-add-method-wizard"></a><a name="_core_adding_a_custom_method_with_classwizard"></a>使用 Add 方法 Wizard 新增自訂方法

下列程式示範如何將自訂方法 PtInCircle 新增至 ActiveX 控制項的基本架構程式碼。 PtInCircle 會判斷傳遞至控制項的座標是否在圓形內部或外部。 這個相同的程式也可以用來新增其他自訂方法。 將您的自訂方法名稱及其參數取代為 PtInCircle 方法名稱和參數。

> [!NOTE]
> 這個範例會使用發行項 `InCircle` 事件中的函數。 如需此函式的詳細資訊，請參閱[MFC ActiveX 控制項：將自訂事件加入至 ActiveX 控制項一](mfc-activex-controls-adding-custom-events.md)文。

#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>使用 Add 方法 Wizard 新增 PtInCircle 自訂方法

1. 載入控制項的專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快捷方式功能表按一下 [**新增**]，然後按一下 [**加入方法**]。

   這會開啟 [新增方法嚮導]。

1. 在 [**方法名稱**] 方塊中，輸入*PtInCircle*。

1. 在 [**內部名稱**] 方塊中，輸入方法內建函式的名稱，或使用預設值（在此案例中為*PtInCircle*）。

1. 在 [傳回**型**別] 方塊中，按一下方法的傳回型別 [ **VARIANT_BOOL** ]。

1. 使用 [**參數類型**] 和 [**參數名稱**] 控制項，新增名為*xCoord*的參數（類型*OLE_XPOS_PIXELS*）。

1. 使用 [**參數類型**] 和 [**參數名稱**] 控制項，新增名為*yCoord*的參數（類型*OLE_YPOS_PIXELS*）。

1. 按一下 [完成] 。

## <a name="add-method-wizard-changes-for-custom-methods"></a><a name="_core_classwizard_changes_for_custom_methods"></a>新增自訂方法的方法嚮導變更

當您新增自訂方法時，[新增方法嚮導] 會對控制項類別標頭（進行一些變更。H）和實（。CPP）檔案。 下列這一行會加入至控制項類別標頭中的分派對應宣告（。H）檔案：

[!code-cpp[NVC_MFC_AxUI#18](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]

此程式碼會宣告稱為的分派方法處理常式 `PtInCircle` 。 控制項使用者可以使用外部名稱呼叫這個函式 `PtInCircle` 。

下面這一行會加入至控制項的。IDL 檔案：

[!code-cpp[NVC_MFC_AxUI#19](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]

這一行會 `PtInCircle` 在 Add 方法 Wizard 方法和 properties 清單中，將特定識別碼指派給方法的位置。 因為已使用 [加入方法] Wizard 來加入自訂方法，所以它的專案會自動加入至專案的。IDL 檔案。

此外，下面這一行位於執行中（。CPP）檔案的控制項類別，會新增至控制項的分派對應：

[!code-cpp[NVC_MFC_AxUI#20](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]

DISP_FUNCTION 宏會將方法對應 `PtInCircle` 至控制項的處理函式、宣告 `PtInCircle` 要**VARIANT_BOOL**的傳回型別，並宣告兩個型別為**VTS_XPOS_PIXELS**的參數和要傳遞至的**VTS_YPOSPIXELS** `PtInCircle` 。

最後，Add 方法 Wizard 會將 stub 函式加入 `CSampleCtrl::PtInCircle` 至控制項的執行底部（。CPP）檔案。 為了讓 `PtInCircle` 能夠如先前所述運作，您必須修改它，如下所示：

[!code-cpp[NVC_MFC_AxUI#21](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)<br/>
[類別檢視和物件瀏覽器圖示](/visualstudio/ide/class-view-and-object-browser-icons)
