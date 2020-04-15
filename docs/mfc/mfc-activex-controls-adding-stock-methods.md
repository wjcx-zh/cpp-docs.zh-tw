---
title: MFC ActiveX 控制項：加入內建方法
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
ms.openlocfilehash: ec59ccc0cbd48fc3114eb2dc0833dd3dd65691de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364676"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>MFC ActiveX 控制項：加入內建方法

stock 方法不同於自定義方法,因為它已經由類[COleControl](../mfc/reference/colecontrol-class.md)實現。 例如,`COleControl`包含支援控制項的刷新方法的預定義成員函數。 此庫存方法的調度映射條目DISP_STOCKFUNC_REFRESH。

>[!IMPORTANT]
> ActiveX 是一種不應用於新開發的傳統技術。 有關取代 ActiveX 的現代技術的詳細資訊,請參閱[ActiveX 控制件](activex-controls.md)。

`COleControl`支援兩種庫存方法:DoClick 和刷新。 控件的用戶調用刷新以立即更新控件的外觀;調用 DoClick 以觸發控制件的單擊事件。

|方法|排程對應項目|註解|
|------------|------------------------|-------------|
|`DoClick`|**DISP_STOCKPROP_DOCLICK)**|觸發單擊事件。|
|`Refresh`|**DISP_STOCKPROP_REFRESH)**|立即更新控件的外觀。|

## <a name="adding-a-stock-method-using-the-add-method-wizard"></a><a name="_core_adding_a_stock_method_using_classwizard"></a>使用新增方法精靈新增庫存方法

使用[添加方法嚮導](../ide/add-method-wizard.md)添加庫存方法非常簡單。 以下過程演示了將刷新方法添加到使用 MFC ActiveX 控制嚮導創建的控制項。

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>使用新增方法精靈新增庫存刷新方法

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 在快捷選單中,按一下「**添加**」,然後按下「**添加方法**」。

   這將打開"添加方法嚮導」。。

1. 在 **「方法名稱」** 框中,按下 **「刷新**」。。

1. 按一下 [完成] 。

## <a name="add-method-wizard-changes-for-stock-methods"></a><a name="_core_classwizard_changes_for_stock_methods"></a>新增庫存方法的方法精靈變更

由於控制項的基項支援股票刷新方法,**因此 Add 方法精靈**不會以任何方式更改控制項的類聲明。 它將此方法的項目加入到控制的調度映射及其 。IDL 檔。 以下行將添加到控件的調度映射中,位於其實現 (中。CPP) 檔案:

[!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

這使刷新方法可供控件的使用者使用。

以下行將新增到控制項的 。IDL 檔案:

[!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

此行為刷新方法指定特定的 ID 號。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)
