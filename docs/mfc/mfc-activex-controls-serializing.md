---
title: MFC ActiveX 控制項： 序列化 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- _wVerMinor
- DoPropExchange
- _wVerMajor
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cf2568561e3e79eaf7c2f56b0b571f5c9e74f268
ms.sourcegitcommit: a3c9e7888b8f437a170327c4c175733ad9eb0454
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2018
ms.locfileid: "50204518"
---
# <a name="mfc-activex-controls-serializing"></a>MFC ActiveX 控制項：序列化

這篇文章討論如何序列化 ActiveX 控制項。 序列化是讀取或寫入至永續性儲存體媒體，例如磁碟檔案的程序。 Microsoft Foundation Class (MFC) 程式庫類別中的序列化提供內建支援`CObject`。 `COleControl` 這將支援延伸到透過內容交換機制使用的 ActiveX 控制項。

>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需有關取代 ActiveX 的現代技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

適用於 ActiveX 控制項的序列化藉由覆寫[COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange)。 此函式，在載入期間呼叫，並儲存的控制項物件，將實作的成員變數或變更通知的成員變數的所有屬性。

下列主題涵蓋的相關序列化 ActiveX 控制項的主要問題：

- 實作`DoPropExchange`序列化控制物件的函式

- [自訂序列化程序](#_core_customizing_the_default_behavior_of_dopropexchange)

- [實作版本支援](#_core_implementing_version_support)

##  <a name="_core_implementing_the_dopropexchange_function"></a> 實作 DoPropExchange 函式

當您使用 ActiveX 控制項精靈產生的控制專案時，數個預設處理常式函式會自動加入至控制項類別，包括的預設實作[COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange)。 下列範例示範使用 ActiveX 控制項精靈 」 建立的類別加入的程式碼：

[!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

如果您想要將屬性設為持續性，修改`DoPropExchange`藉由新增屬性交換函式的呼叫。 下列範例示範自訂的布林 CircleShape 屬性，其中 CircleShape 屬性具有預設值是序列化 **，則為 TRUE**:

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

下表列出可用來序列化控制項的屬性可能的屬性交換函式：

|屬性交換函式|用途|
|---------------------------------|-------------|
|**PX_Blob （)**|將序列化的二進位大型物件 (BLOB) 資料屬性的型別。|
|**PX_Bool （)**|將序列化的類型為布林值屬性。|
|**PX_Color （)**|將序列化的類型色彩屬性。|
|**PX_Currency （)**|序列化型別的**CY** （貨幣） 屬性。|
|**PX_Double （)**|序列化型別的**double**屬性。|
|**PX_Font （)**|將序列化字型類型的屬性。|
|**PX_Float （)**|序列化型別的**浮點數**屬性。|
|**PX_IUnknown （)**|將序列化的型別屬性`LPUNKNOWN`。|
|**PX_Long （)**|序列化型別的**長**屬性。|
|**PX_Picture （)**|序列化型別的圖片屬性。|
|**PX_Short （)**|序列化型別的**簡短**屬性。|
|**PXstring （)**|序列化型別的`CString`屬性。|
|**PX_ULong （)**|序列化型別的**ULONG**屬性。|
|**PX_UShort （)**|序列化型別的**USHORT**屬性。|

如需有關這些屬性交換函式的詳細資訊，請參閱 <<c0> [ 持續性的 OLE 控制項](../mfc/reference/persistence-of-ole-controls.md)中*MFC 參考 》*。

##  <a name="_core_customizing_the_default_behavior_of_dopropexchange"></a> 自訂 DoPropExchange 的預設行為

預設實作`DoPropertyExchange`（如前一個主題中所示） 中，會呼叫基底類別`COleControl`。 這將會序列化自動所支援的屬性`COleControl`，它會使用更多的儲存體空間序列化在控制項的自訂屬性。 移除這個呼叫，可讓您只在您認為重要的屬性進行序列化的物件。 控制項已實作的任何內建屬性狀態不會序列化時儲存或載入的控制項物件，除非您明確地新增**PX_** 呼叫它們。

##  <a name="_core_implementing_version_support"></a> 實作版本支援

版本支援讓修改過的 ActiveX 控制項，以新增新的持續性屬性，而且仍然能夠偵測並載入控制項的舊版本所建立的永續性狀態。 若要讓控制項的版本可供隨著持續性資料的詳細資訊，請呼叫[COleControl::ExchangeVersion](../mfc/reference/colecontrol-class.md#exchangeversion)控制項的`DoPropExchange`函式。 如果使用 ActiveX 控制項精靈 」 來建立 「 ActiveX 控制項，會自動插入這個呼叫。 如果不需要的版本支援，也可以加以移除。 不過，控制項大小的成本是很小 （4 個位元組） 的版本支援可提供額外的彈性。

如果控制項不是使用 ActiveX 控制項精靈，將呼叫加入`COleControl::ExchangeVersion`插入下面這一行的開頭您`DoPropExchange`函式 (呼叫前面`COleControl::DoPropExchange`):

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

您可以使用任何**DWORD**做為版本號碼。 ActiveX 控制項精靈所產生的專案使用`_wVerMinor`和`_wVerMajor`為預設值。 這些是定義專案的 ActiveX 控制項類別的實作檔案中的全域常數。 中的其餘部分您`DoPropExchange`函式，您可以呼叫[CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion)隨時擷取您要儲存或擷取的版本。

在下列範例中，此範例控制項的第 1 版會有"ReleaseDate"屬性。 第 2 版，將 「 OriginalDate"屬性。 如果控制項指示載入持續性的狀態從舊的版本，它會初始化為預設值的新屬性的成員變數。

[!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

根據預設，控制項 」 「 舊將資料轉換成最新的格式。 例如，如果控制項的第 2 版中載入第 1 版所儲存的資料，它會寫入第 2 版格式一次儲存時。 如果您想要在上一個讀取的格式儲存資料的控制項，則會傳遞**假**做為第三個參數呼叫時`ExchangeVersion`。 此第三個參數是選擇性的而且是 **，則為 TRUE**預設。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)

