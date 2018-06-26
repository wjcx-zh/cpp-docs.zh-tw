---
title: MFC ActiveX 控制項： 序列化 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: f9db6ff6c0cdda01875e4968e4d92ca087ad2b57
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930057"
---
# <a name="mfc-activex-controls-serializing"></a>MFC ActiveX 控制項：序列化
本文將討論如何將 ActiveX 控制項。 序列化是讀取或寫入至永續性儲存體中，例如磁碟檔案的程序。 Microsoft Foundation Class (MFC) 程式庫中類別的序列化提供內建支援`CObject`。 `COleControl` 擴充此一支援透過內容交換機制使用的 ActiveX 控制項。  
  
 序列化為 ActiveX 控制項藉由覆寫[COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange)。 此函式，在載入期間呼叫，並儲存的控制項物件，將實作的成員變數或成員變數，以變更通知的所有屬性。  
  
 下列主題涵蓋與序列化 ActiveX 控制項相關的主要問題：  
  
-   實作`DoPropExchange`序列化控制物件的函式  
  
-   [自訂序列化程序](#_core_customizing_the_default_behavior_of_dopropexchange)  
  
-   [實作版本支援](#_core_implementing_version_support)  
  
##  <a name="_core_implementing_the_dopropexchange_function"></a> 實作 DoPropExchange 函式  
 當您使用 ActiveX 控制項精靈來產生控制項專案時，數個預設處理常式函式會自動加入至控制項類別，包括的預設實作[COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange)。 下列範例會顯示加入至類別，使用 ActiveX 控制項精靈 」 建立的程式碼：  
  
 [!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]  
  
 如果您想要讓屬性持續性，修改`DoPropExchange`加屬性交換函式的呼叫。 下列範例會示範自訂布林 CircleShape 屬性之 CircleShape 屬性具有預設值是序列化**TRUE**:  
  
 [!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]  
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]  
  
 下表列出您可以使用控制項的屬性進行序列化可能屬性交換函式：  
  
|屬性交換函式|用途|  
|---------------------------------|-------------|  
|**PX_Blob （)**|序列化型別的二進位大型物件 (BLOB) 資料屬性。|  
|**PX_Bool （)**|將序列化的類型為布林值屬性。|  
|**PX_Color （)**|將序列化的類型色彩屬性。|  
|**PX_Currency （)**|序列化型別的**CY** （貨幣） 屬性。|  
|**PX_Double （)**|序列化型別的**double**屬性。|  
|**PX_Font （)**|將序列化字型類型的屬性。|  
|**PX_Float （)**|序列化型別的**float**屬性。|  
|**PX_IUnknown （)**|將序列化型別的屬性`LPUNKNOWN`。|  
|**PX_Long （)**|序列化型別的**長**屬性。|  
|**PX_Picture （)**|序列化型別的圖片屬性。|  
|**PX_Short （)**|序列化型別的**簡短**屬性。|  
|**PXstring （)**|序列化型別的`CString`屬性。|  
|**PX_ULong （)**|序列化型別的**ULONG**屬性。|  
|**PX_UShort （)**|序列化型別的**USHORT**屬性。|  
  
 如需有關這些屬性交換函式的詳細資訊，請參閱[持續性的 OLE 控制項的](../mfc/reference/persistence-of-ole-controls.md)中*MFC 參考*。  
  
##  <a name="_core_customizing_the_default_behavior_of_dopropexchange"></a> 自訂 DoPropExchange 的預設行為  
 預設實作`DoPropertyExchange`（如先前的主題中所示） 會呼叫基底類別`COleControl`。 這將會序列化的屬性會自動受到`COleControl`，它會使用更多的儲存空間比序列化控制項的自訂屬性。 移除這個呼叫可讓您只在您認為重要的屬性進行序列化的物件。 當儲存或載入控制項物件，除非您明確地新增控制項已實作的任何內建屬性狀態不會序列化**PX_** 呼叫它們。  
  
##  <a name="_core_implementing_version_support"></a> 實作版本支援  
 版本支援讓修改過的 ActiveX 控制項，加入新的持續性屬性，而且仍然能夠偵測並載入控制項的較早版本所建立的永續性狀態。 若要讓控制項的版本可供其永續性資料的一部分，呼叫[COleControl::ExchangeVersion](../mfc/reference/colecontrol-class.md#exchangeversion)控制項的`DoPropExchange`函式。 如果使用 ActiveX 控制項精靈 」 來建立 「 ActiveX 控制項，此呼叫會自動插入。 如果不需要版本支援，也可以加以移除。 不過，在控制項大小的成本很小 （4 個位元組） 的版本支援可提供增加更多彈性。  
  
 如果控制項不是使用 ActiveX 控制項精靈，將呼叫加入`COleControl::ExchangeVersion`的開頭插入下行程式`DoPropExchange`函式 (再呼叫`COleControl::DoPropExchange`):  
  
 [!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]  
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]  
  
 您可以使用任何**DWORD**做為版本號碼。 ActiveX 控制項精靈所產生的專案使用`_wVerMinor`和`_wVerMajor`作為預設值。 這些是定義專案的 ActiveX 控制項類別的實作檔中的全域常數。 中的其餘部分您`DoPropExchange`函式，您可以呼叫[CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion)隨時擷取您要儲存或擷取的版本。  
  
 在下列範例中，此範例控制項的第 1 版有"ReleaseDate"屬性。 第 2 版，將 「 OriginalDate"屬性。 如果控制項指示從舊的版本載入永續性狀態，它會初始化為預設值的新屬性的成員變數。  
  
 [!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]  
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]  
  
 根據預設，控制項 」"舊資料轉換成最新格式。 例如，如果控制項的第 2 版載入第 1 版中所儲存的資料，它會寫入第 2 版格式一次儲存時。 如果您想要在上一個讀取的格式儲存資料的控制項，則傳遞**FALSE**做為第三個參數呼叫時`ExchangeVersion`。 此第三個參數是選擇性，而且是**TRUE**預設。  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)

