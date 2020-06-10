---
title: MFC ActiveX 控制項：加入內建方法
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
ms.openlocfilehash: 42d8dfecd32b4aecd0daa4034497ec9abff6d11a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619931"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>MFC ActiveX 控制項：加入內建方法

內建方法與自訂方法不同之處在于，它已經由類別[COleControl](reference/colecontrol-class.md)所實作為。 例如， `COleControl` 包含可支援控制項之 Refresh 方法的預先定義成員函式。 此 stock 方法的分派對應專案為 DISP_STOCKFUNC_REFRESH。

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需取代 ActiveX 之新式技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

`COleControl`支援兩種內建方法： DoClick 和 Refresh。 重新整理是由控制項的使用者叫用，以立即更新控制項的外觀;叫用 DoClick 以引發控制項的 Click 事件。

|方法|分派對應專案|註解|
|------------|------------------------|-------------|
|`DoClick`|**DISP_STOCKPROP_DOCLICK （）**|引發 Click 事件。|
|`Refresh`|**DISP_STOCKPROP_REFRESH （）**|立即更新控制項的外觀。|

## <a name="adding-a-stock-method-using-the-add-method-wizard"></a><a name="_core_adding_a_stock_method_using_classwizard"></a>使用 Add 方法 Wizard 加入內建方法

使用 [[新增方法嚮導]](../ide/add-method-wizard.md)，即可輕鬆加入內建方法。 下列程式示範如何將 Refresh 方法新增至使用 MFC ActiveX 控制項 Wizard 所建立的控制項。

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>使用 Add 方法 Wizard 新增 stock Refresh 方法

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快捷方式功能表按一下 [**新增**]，然後按一下 [**加入方法**]。

   這會開啟 [新增方法嚮導]。

1. 在 [**方法名稱**] 方塊中 **，按一下 [** 重新整理]。

1. 按一下 [完成] 。

## <a name="add-method-wizard-changes-for-stock-methods"></a><a name="_core_classwizard_changes_for_stock_methods"></a>為內建方法新增方法嚮導變更

由於控制項的基類支援 stock Refresh 方法，因此 [**加入方法] Wizard**不會以任何方式變更控制項的類別宣告。 它會將方法的專案新增至控制項的分派對應和其。IDL 檔案。 下面這一行會加入控制項的「分派對應」（位於其實作為）中（。CPP）檔案：

[!code-cpp[NVC_MFC_AxUI#16](codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

這會讓控制項的使用者可以使用 Refresh 方法。

下面這一行會加入至控制項的。IDL 檔案：

[!code-cpp[NVC_MFC_AxUI#17](codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

這一行會為 Refresh 方法指派特定的識別碼。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)
