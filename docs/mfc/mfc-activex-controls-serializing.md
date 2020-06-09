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
ms.openlocfilehash: c06299f2fc7409476e4f5e5744ea11c962e3b173
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621192"
---
# <a name="mfc-activex-controls-serializing"></a>MFC ActiveX 控制項：序列化

本文討論如何序列化 ActiveX 控制項。 序列化是讀取或寫入持續性儲存媒體（例如磁片檔案）的程式。 Microsoft Foundation Class （MFC）程式庫提供類別中序列化的內建支援 `CObject` 。 `COleControl`透過使用屬性交換器制，將這項支援延伸至 ActiveX 控制項。

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需取代 ActiveX 之新式技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

ActiveX 控制項的序列化是藉由覆寫[COleControl：:D opropexchange](reference/colecontrol-class.md#dopropexchange)來執行。 這個函式在載入和儲存控制項物件期間呼叫，會儲存以成員變數或成員變數（具有變更通知）來執行的所有屬性。

下列主題涵蓋序列化 ActiveX 控制項的主要相關問題：

- 執行函式 `DoPropExchange` 以序列化控制項物件

- [自訂序列化程式](#_core_customizing_the_default_behavior_of_dopropexchange)

- [執行版本支援](#_core_implementing_version_support)

## <a name="implementing-the-dopropexchange-function"></a><a name="_core_implementing_the_dopropexchange_function"></a>執行 DoPropExchange 函式

當您使用 ActiveX Control Wizard 來產生控制項專案時，會自動將數個預設的處理常式函式新增至控制項類別，包括 COleControl 的預設執行[：:D opropexchange](reference/colecontrol-class.md#dopropexchange)。 下列範例顯示新增至使用 ActiveX 控制項 Wizard 建立之類別的程式碼：

[!code-cpp[NVC_MFC_AxUI#43](codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

如果您想要將屬性設為持續性，請 `DoPropExchange` 將呼叫新增至屬性交換函式來進行修改。 下列範例示範自訂布林 CircleShape 屬性的序列化，其中 CircleShape 屬性的預設值為**TRUE**：

[!code-cpp[NVC_MFC_AxSer#1](codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

下表列出您可以用來序列化控制項屬性的可能屬性交換函數：

|屬性交換函式|目的|
|---------------------------------|-------------|
|**PX_Blob （）**|序列化類型二進位大型物件（BLOB）資料屬性。|
|**PX_Bool （）**|序列化類型的布林值屬性。|
|**PX_Color （）**|序列化類型色彩屬性。|
|**PX_Currency （）**|序列化類型**CY** （貨幣）屬性。|
|**PX_Double （）**|序列化**double**屬性型別。|
|**PX_Font （）**|序列化字型類型屬性。|
|**PX_Float （）**|序列化類型**float**屬性。|
|**PX_IUnknown （）**|序列化類型的屬性 `LPUNKNOWN` 。|
|**PX_Long （）**|序列化類型**long**屬性。|
|**PX_Picture （）**|序列化類型圖片屬性。|
|**PX_Short （）**|序列化類型的**short**屬性。|
|**PXstring( )**|序列化類型 `CString` 屬性。|
|**PX_ULong （）**|序列化類型**ULONG**屬性。|
|**PX_UShort （）**|序列化類型**USHORT**屬性。|

如需這些屬性交換函數的詳細資訊，請參閱*MFC 參考*中[的 OLE 控制項的持續](reference/persistence-of-ole-controls.md)性。

## <a name="customizing-the-default-behavior-of-dopropexchange"></a><a name="_core_customizing_the_default_behavior_of_dopropexchange"></a>自訂 DoPropExchange 的預設行為

的預設執行 `DoPropertyExchange` （如前一個主題所示）會呼叫基類 `COleControl` 。 這會序列化所自動支援的屬性集 `COleControl` ，其使用的儲存空間比只序列化控制項的自訂屬性更多。 移除此呼叫可讓您的物件只序列化您認為重要的屬性。 除非您明確地加入控制項物件的**PX_** 呼叫，否則在儲存或載入 control 物件時，不會序列化控制項已實作為的任何內建屬性狀態。

## <a name="implementing-version-support"></a><a name="_core_implementing_version_support"></a>執行版本支援

版本支援可讓修訂的 ActiveX 控制項加入新的持續性屬性，而且仍然能夠偵測和載入舊版控制項所建立的持續性狀態。 若要讓控制項的版本可作為其持續性資料的一部分，請在控制項的函式中呼叫[COleControl：： ExchangeVersion](reference/colecontrol-class.md#exchangeversion) `DoPropExchange` 。 如果 ActiveX 控制項是使用 ActiveX Control Wizard 建立的，則會自動插入此呼叫。 如果不需要版本支援，可以將它移除。 不過，控制項大小的成本非常小（4個位元組），以提供版本支援所提供的額外彈性。

如果不是使用 ActiveX 控制項 Wizard 來建立控制項，請在函式 `COleControl::ExchangeVersion` 的開頭插入下列這一行 `DoPropExchange` （在呼叫之前），藉以新增的呼叫 `COleControl::DoPropExchange` ：

[!code-cpp[NVC_MFC_AxSer#1](codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

您可以使用任何**DWORD**做為版本號碼。 ActiveX 控制項嚮導產生的專案會使用 `_wVerMinor` 和 `_wVerMajor` 做為預設值。 這些是在專案的 ActiveX 控制項類別的實檔案中定義的全域常數。 在函式的其餘部分中 `DoPropExchange` ，您可以隨時呼叫[CPropExchange：： GetVersion](reference/cpropexchange-class.md#getversion) ，以取得您要儲存或抓取的版本。

在下列範例中，此範例控制項的第1版只有 "ReleaseDate" 屬性。 第2版會新增 "OriginalDate" 屬性。 如果指示控制項從舊版本載入持續性狀態，則會將新屬性的成員變數初始化為預設值。

[!code-cpp[NVC_MFC_AxSer#4](codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

根據預設，控制項會將舊資料轉換成最新的格式。 例如，如果控制項的第2版載入第1版所儲存的資料，則會在再次儲存時寫入第2版格式。 如果您想要讓控制項以上次讀取的格式儲存資料，請在呼叫時傳遞**FALSE**做為第三個參數 `ExchangeVersion` 。 第三個參數是選擇性的，而且預設為**TRUE** 。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)
