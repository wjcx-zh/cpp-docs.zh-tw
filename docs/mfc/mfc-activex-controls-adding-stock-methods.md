---
title: MFC ActiveX 控制項：加入內建方法
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
ms.openlocfilehash: b4b01e4fb202cfd7a923d22cb57ce5ec6988e11d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502275"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>MFC ActiveX 控制項：加入內建方法

Stock 方法與自訂方法不同之處在于，它已經由類別 [COleControl](reference/colecontrol-class.md)實作為。 例如， `COleControl` 包含預先定義的成員函式，可支援您控制項的重新整理方法。 此 stock 方法的分派對應專案是 DISP_STOCKFUNC_REFRESH。

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需有關取代 ActiveX 之新式技術的詳細資訊，請參閱 [Activex 控制項](activex-controls.md)。

`COleControl` 支援兩種內建方法： DoClick 和重新整理。 重新整理是由控制項的使用者叫用，以立即更新控制項的外觀;叫用 DoClick 來引發控制項的 Click 事件。

|方法|分派對應專案|註解|
|------------|------------------------|-------------|
|`DoClick`|**DISP_STOCKPROP_DOCLICK ( ) **|引發 Click 事件。|
|`Refresh`|**DISP_STOCKPROP_REFRESH ( ) **|立即更新控制項的外觀。|

## <a name="adding-a-stock-method-using-the-add-method-wizard"></a><a name="_core_adding_a_stock_method_using_classwizard"></a> 使用 Add 方法 Wizard 新增股票方法

使用 [ [新增方法] Wizard](../ide/adding-a-method-visual-cpp.md#add-method-wizard)可簡化加入 stock 方法的工作。 下列程式示範如何將 Refresh 方法新增至使用 MFC ActiveX 控制項 Wizard 建立的控制項。

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>使用 Add 方法 Wizard 新增股票重新整理方法

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快捷方式功能表按一下 [ **加入** ]，然後按一下 [ **加入方法**]。

   這會開啟 [新增方法] Wizard。

1. 在 [ **方法名稱** ] 方塊中 **，按一下 [** 重新整理]。

1. 按一下 [完成] 。

## <a name="add-method-wizard-changes-for-stock-methods"></a><a name="_core_classwizard_changes_for_stock_methods"></a> 新增內建方法的方法嚮導變更

因為控制項的基類支援內建重新整理方法，所以 [ **加入方法] Wizard** 不會以任何方式變更控制項的類別宣告。 它會將方法的專案加入至控制項的分派對應和其。IDL 檔案。 下一行會加入至控制項的分派對應，其在其實 ( 中。CPP) 檔案：

[!code-cpp[NVC_MFC_AxUI#16](codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

這會讓控制項的使用者可以使用重新整理方法。

下一行會加入至控制項的。IDL 檔案：

[!code-cpp[NVC_MFC_AxUI#17](codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

這一行會將特定識別碼指派給 Refresh 方法。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)
