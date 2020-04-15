---
title: MFC ActiveX 控制項：序列化
ms.date: 09/12/2018
f1_keywords:
- _wVerMinor
- DoPropExchange
- _wVerMajor
helpviewer_keywords:
- MFC ActiveX controls [MFC], version support
- wVerMinor global constant [MFC]
- GetVersion method [MFC]
- ExchangeVersion method [MFC]
- MFC ActiveX controls [MFC], serializing
- DoPropExchange method [MFC]
- versioning ActiveX controls
- wVerMajor global constant
ms.assetid: 9d57c290-dd8c-4853-b552-6f17f15ebedd
ms.openlocfilehash: d804486b612906f537b6ed1665dfc0cec5149826
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364541"
---
# <a name="mfc-activex-controls-serializing"></a>MFC ActiveX 控制項：序列化

本文討論如何序列化 ActiveX 控制項。 序列化是從持久存儲媒體(如磁碟檔)讀取或寫入的過程。 微軟基礎類 (MFC) 庫`CObject`為類 中的序列化提供了內置支援。 `COleControl`使用屬換機制將此支援擴展到 ActiveX 控制件。

>[!IMPORTANT]
> ActiveX 是一種不應用於新開發的傳統技術。 有關取代 ActiveX 的現代技術的詳細資訊,請參閱[ActiveX 控制件](activex-controls.md)。

ActiveX 控制項序列化是透過重寫[COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange)實現的。 此函數在載入和保存控制項件物件期間調用,儲存使用成員變數或成員變數實現的所有屬性以及更改通知。

以下主題涵蓋與序列化 ActiveX 控制項相關的主要問題:

- 實現`DoPropExchange`對控制元件物件進行序列化的功能

- [自訂序列化程序](#_core_customizing_the_default_behavior_of_dopropexchange)

- [實現版本支援](#_core_implementing_version_support)

## <a name="implementing-the-dopropexchange-function"></a><a name="_core_implementing_the_dopropexchange_function"></a>完整 DoPropExchange 功能

當您使用 ActiveX 控制件精靈生成控制項專案時,多個預設處理程式函數將自動添加到控制項類別中,包括[COleControl::Do PropExchange](../mfc/reference/colecontrol-class.md#dopropexchange)的預設實現。 以下範例顯示新增到使用 ActiveX 控制項精靈建立的類別的程式碼:

[!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

如果要使屬性持久化,請通過向屬性`DoPropExchange`交換函數添加調用進行修改。 下面的範例展示自訂布林元件屬性的序列化,其中 CircleShape 屬性的預設值為**TRUE**:

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

下表列出了可用於序列化控制屬性的可能屬換函數:

|屬換功能|目的|
|---------------------------------|-------------|
|**PX_Blob)**|序列化類型二進位元物件 (BLOB) 資料屬性。|
|**PX_Bool)**|序列化布爾屬性類型。|
|**PX_Color)**|序列化類型顏色屬性。|
|**PX_Currency)**|序列化類型**CY(** 貨幣)屬性。|
|**PX_Double)**|序列化型**態 雙屬性**。|
|**PX_Font)**|序列化字體類型屬性。|
|**PX_Float)**|序列化類型**浮動**屬性。|
|**PX_IUnknown)**|序列化類型`LPUNKNOWN`的屬性。|
|**PX_Long)**|序列化類型**長**屬性。|
|**PX_Picture)**|序列化類型圖片屬性。|
|**PX_Short)**|序列化類型**短**屬性。|
|**PXstring( )**|序列化類型`CString`屬性。|
|**PX_ULong)**|序列化類型**ULONG**屬性。|
|**PX_UShort)**|序列化類型**USHORT**屬性。|

有關這些屬換函數的詳細資訊,請參閱*MFC 參考*中的[OLE 控制項持久性](../mfc/reference/persistence-of-ole-controls.md)。

## <a name="customizing-the-default-behavior-of-dopropexchange"></a><a name="_core_customizing_the_default_behavior_of_dopropexchange"></a>自訂 DoPropExchange 的預設行為

的`DoPropertyExchange`默認實現(如上一個主題所示)對基`COleControl`類 進行調用。 這將序列化`COleControl`由 自動支援的屬性集,該屬性使用比僅序列化控制件的自定義屬性更多的儲存空間。 刪除此呼叫允許物件僅序列化您認為重要的屬性。 保存或載入控制項物件時,不會序列化控制項已實現的任何股票屬性,除非您顯式添加**PX_** 調用它們。

## <a name="implementing-version-support"></a><a name="_core_implementing_version_support"></a>實現版本支援

版本支援使修訂後的 ActiveX 控制件能夠添加新的持久性屬性,並且仍然能夠檢測和載入控制項的早期版本創建的持久狀態。 要使控制項的版本作為其持久資料的一部分可用,請調用控制項`DoPropExchange`函數中的[COleControl::ExchangeVersion。](../mfc/reference/colecontrol-class.md#exchangeversion) 如果使用 ActiveX 控制精靈創建 ActiveX 控制件,則會自動插入此調用。 如果不需要版本支援,可以將其刪除。 但是,對於版本支援提供的額外靈活性,控制大小的成本非常小(4 位元組)。

如果未使用 ActiveX 控制件精靈建立控制項`COleControl::ExchangeVersion`, 請`DoPropExchange`透過在函數開頭插入以下行(在調用`COleControl::DoPropExchange`之前) 添加調用。

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

您可以使用任何**DWORD**作為版本號。 由 ActiveX 控制件精靈生成的`_wVerMinor`專案`_wVerMajor`使用並作為預設值。 這些是在專案 ActiveX 控制項類的實現檔中定義的全域常量。 在`DoPropExchange`函數的其餘部分中,您可以隨時調用[CPropExchange:GetVersion](../mfc/reference/cpropexchange-class.md#getversion)檢索要保存或檢索的版本。

在下面的示例中,此示例控件的版本 1 僅具有"發佈日期"屬性。 版本 2 添加了「原始日期」屬性。 如果指示控制項從舊版本中載入持久狀態,它將新屬性的成員變數初始化為預設值。

[!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

預設情況下,控制項會將舊資料轉換為「最新格式。 例如,如果控件的版本 2 載入由版本 1 保存的資料,則當再次儲存版本 2 格式時,它將編寫版本 2 格式。 如果希望控制檔在上次讀取時以格式保存資料,則在調用**FALSE**`ExchangeVersion`時將 FALSE 作為第三個參數傳遞。 此第三個參數是可選的,預設情況下為**TRUE。**

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)
