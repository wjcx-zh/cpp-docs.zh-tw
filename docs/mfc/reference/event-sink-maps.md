---
title: "事件接收對應 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- event sink maps
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 33bf66d18b499787a34b2da501bb3e8ead255459
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="event-sink-maps"></a>事件接收對應
當內嵌的 OLE Automation 控制項引發某個事件時，控制項的容器會使用由 MFC 提供的機制 (稱為「事件接收對應」) 來接收事件。 這個事件接收對應會指定每個特定事件的處理常式，以及那些事件函式的參數。 如需事件接收對應的詳細資訊，請參閱文章[ActiveX 控制項容器](../../mfc/activex-control-containers.md)。  
  
### <a name="event-sink-maps"></a>事件接收對應  
  
|||  
|-|-|  
|[BEGIN_EVENTSINK_MAP](#begin_eventsink_map)|事件接收對應定義的開頭。|  
|[DECLARE_EVENTSINK_MAP](#declare_eventsink_map)|宣告事件接收對應。|  
|[END_EVENTSINK_MAP](#end_eventsink_map)|事件接收對應定義的結尾。|  
|[ON_EVENT](#on_event)|定義特定事件的事件處理常式。|  
|[ON_EVENT_RANGE](#on_event_range)|定義一組 OLE 控制項所引發特定事件的事件處理常式。|  
|[ON_EVENT_REFLECT](#on_event_reflect)|在由控制項的容器處理之前，接收控制項引發的事件。|  
|[ON_PROPNOTIFY](#on_propnotify)|定義一個處理常式來處理 OLE 控制項的屬性通知。|  
|[ON_PROPNOTIFY_RANGE](#on_propnotify_range)|定義一個處理常式來處理來自一組 OLE 控制項的屬性通知。|  
|[ON_PROPNOTIFY_REFLECT](#on_propnotify_reflect)|在由控制項的容器處理前，接收控制項傳送的屬性通知。|  
  
##  <a name="begin_eventsink_map"></a>BEGIN_EVENTSINK_MAP  
 開始您的事件接收對應定義。  
  
```   
BEGIN_EVENTSINK_MAP(theClass, baseClass)  
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 指定的事件接收對應的控制項類別的名稱。  
  
 `baseClass`  
 指定 `theClass` 基底類別的名稱。  
  
### <a name="remarks"></a>備註  
 在定義類別成員函式的實作 (.cpp) 檔案，啟動 事件接收對應與`BEGIN_EVENTSINK_MAP`巨集，然後新增巨集項目，每個事件通知，並完成的事件接收對應`END_EVENTSINK_MAP`巨集。  
  
 如需事件接收對應和 OLE 控制項容器的詳細資訊，請參閱文章[ActiveX 控制項容器](../../mfc/activex-control-containers.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdisp.h  
  
##  <a name="declare_eventsink_map"></a>DECLARE_EVENTSINK_MAP  
 OLE 容器可提供事件接收對應至指定的事件會通知您的容器。  
  
```   
DECLARE_EVENTSINK_MAP()   
```  
  
### <a name="remarks"></a>備註  
 使用`DECLARE_EVENTSINK_MAP`巨集，在類別宣告的結尾。 然後，在。CPP 檔案所定義的成員函式類別，請使用`BEGIN_EVENTSINK_MAP`巨集、 巨集項目，每個通知的事件和`END_EVENTSINK_MAP`巨集來宣告事件接收清單的結尾。  
  
 如需事件接收對應的詳細資訊，請參閱文章[ActiveX 控制項容器](../../mfc/activex-control-containers.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  
  
##  <a name="end_eventsink_map"></a>END_EVENTSINK_MAP  
 結束您的事件接收器對應的定義。  
  
```   
END_EVENTSINK_MAP()   
```  
  
### <a name="requirements"></a>需求  
  **標頭**afxdisp.h  
  
##  <a name="on_event"></a>ON_EVENT  
 使用`ON_EVENT`OLE 控制項所引發的巨集來定義事件的事件處理常式函式。  
  
```   
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams) 
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 這個事件接收對應所屬的類別。  
  
 `id`  
 OLE 控制項的控制項 ID。  
  
 `dispid`  
 控制項所引發之事件的分派 ID。  
  
 `pfnHandler`  
 處理事件的成員函式的指標。 此函式應該具有**BOOL**傳回型別和參數型別符合事件的參數 (請參閱`vtsParams`)。 函式應傳回**TRUE**指出事件已處理，否則**FALSE**。  
  
 `vtsParams`  
 一系列**VTS_**常數，指定事件的參數型別。 這些都是相同的常數，例如用於分派對應項目`DISP_FUNCTION`。  
  
### <a name="remarks"></a>備註  
 `vtsParams`引數是以空格分隔的清單中的值**VTS_**常數。 一或多個以空格 （不是逗號） 分隔這些值會指定函式的參數清單。 例如:   
  
 [!code-cpp[NVC_MFCAutomation #&11;](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 指定清單，其中包含短整數，後面接著**BOOL**。  
  
 如需清單**VTS_**常數，請參閱[EVENT_CUSTOM](event-maps.md#event_custom)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdisp.h  
  
##  <a name="on_event_range"></a>ON_EVENT_RANGE  
 使用`ON_EVENT_RANGE`任何具有連續的識別碼範圍內的控制項 ID 的 OLE 控制項所引發的巨集來定義事件的事件處理常式函式。  
  
```   
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)   
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 這個事件接收對應所屬的類別。  
  
 `idFirst`  
 範圍中的第一個 OLE 控制項的控制項 ID。  
  
 `idLast`  
 範圍中的最後一個 OLE 控制項的控制項 ID。  
  
 `dispid`  
 控制項所引發之事件的分派 ID。  
  
 `pfnHandler`  
 處理事件的成員函式的指標。 此函式應該具有**BOOL**傳回型別，第一個參數的型別**UINT** （適用於控制項 ID)，以及額外的參數符合事件參數的型別 (請參閱`vtsParams`)。 函式應傳回**TRUE**指出事件已處理，否則**FALSE**。  
  
 `vtsParams`  
 一系列**VTS_**常數，指定事件的參數型別。 第一個常數的類型應為**VTS_I4**，做為控制項的識別碼。 這些都是相同的常數，例如用於分派對應項目`DISP_FUNCTION`。  
  
### <a name="remarks"></a>備註  
 `vtsParams`引數是以空格分隔的清單中的值**VTS_**常數。 一或多個以空格 （不是逗號） 分隔這些值會指定函式的參數清單。 例如:   
  
 [!code-cpp[NVC_MFCAutomation #&11;](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 指定清單，其中包含短整數，後面接著**BOOL**。  
  
 如需清單**VTS_**常數，請參閱[EVENT_CUSTOM](event-maps.md#event_custom)。  
  
### <a name="example"></a>範例  
 下列範例將示範三個控制項實作的 MouseDown 事件的事件處理常式，(`IDC_MYCTRL1`透過`IDC_MYCTRL3`)。 事件處理常式函式`OnRangeMouseDown`，標頭檔的對話方塊類別宣告 ( `CMyDlg`) 做為︰  
  
 [!code-cpp[NVC_MFCAutomation #&12;](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]  
  
 下列程式碼是在對話方塊類別的實作檔中定義。  
  
 [!code-cpp[NVC_MFCAutomation #&13;](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxdisp.h  
  
##  <a name="on_event_reflect"></a>ON_EVENT_REFLECT  
 `ON_EVENT_REFLECT`巨集，用於在事件接收對應的 OLE 控制項的包裝函式類別，接收控制項的容器處理前，由控制項所引發的事件。  
  
```   
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams) 
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 這個事件接收對應所屬的類別。  
  
 dispid  
 控制項所引發之事件的分派 ID。  
  
 `pfnHandler`  
 處理事件的成員函式的指標。 此函式應該具有**BOOL**傳回型別和參數型別符合事件的參數 (請參閱`vtsParams`)。 函式應傳回**TRUE**指出事件已處理，否則**FALSE**。  
  
 `vtsParams`  
 一系列**VTS_**常數，指定事件的參數型別。 這些都是相同的常數，例如用於分派對應項目`DISP_FUNCTION`。  
  
### <a name="remarks"></a>備註  
 `vtsParams`引數是以空格分隔的清單中的值**VTS_**常數。  
  
 一或多個以空格 （不是逗號） 分隔這些值會指定函式的參數清單。 例如：  
  
 [!code-cpp[NVC_MFCAutomation #&11;](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 指定清單，其中包含短整數，後面接著**BOOL**。  
  
 如需清單**VTS_**常數，請參閱[EVENT_CUSTOM](event-maps.md#event_custom)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdisp.h  
  
##  <a name="on_propnotify"></a>ON_PROPNOTIFY  
 使用`ON_PROPNOTIFY`巨集，以定義來處理 OLE 控制項的屬性通知事件接收對應項目。  
  
```   
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 這個事件接收對應所屬的類別。  
  
 `id`  
 OLE 控制項的控制項 ID。  
  
 `dispid`  
 參與通知屬性的分派 ID。  
  
 `pfnRequest`  
 處理成員函式指標**OnRequestEdit**通知，此屬性。 此函式應該具有**BOOL**傳回型別和**BOOL\* **參數。 此函式應該將參數設定為**TRUE**允許要變更的屬性和**FALSE**不允許。 函式應傳回**TRUE**表示通知已處理，否則**FALSE**。  
  
 `pfnChanged`  
 處理成員函式指標**OnChanged**通知，此屬性。 函式應該具有**BOOL**傳回型別和**UINT**參數。 函式應傳回**TRUE**表示通知已處理，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 `vtsParams`引數是以空格分隔的清單中的值**VTS_**常數。 一或多個以空格 （不是逗號） 分隔這些值會指定函式的參數清單。 例如:   
  
 [!code-cpp[NVC_MFCAutomation #&11;](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 指定清單，其中包含短整數，後面接著**BOOL**。  
  
 如需清單**VTS_**常數，請參閱[EVENT_CUSTOM](event-maps.md#event_custom)。  
  
##  <a name="on_propnotify_range"></a>ON_PROPNOTIFY_RANGE  
 使用`ON_PROPNOTIFY_RANGE`巨集，以定義來處理從任何具有連續的識別碼範圍內的控制項 ID 的 OLE 控制項的屬性通知事件接收對應項目。  
  
```  
 
ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 這個事件接收對應所屬的類別。  
  
 `idFirst`  
 範圍中的第一個 OLE 控制項的控制項 ID。  
  
 `idLast`  
 範圍中的最後一個 OLE 控制項的控制項 ID。  
  
 `dispid`  
 參與通知屬性的分派 ID。  
  
 `pfnRequest`  
 處理成員函式指標**OnRequestEdit**通知，此屬性。 此函式應該具有**BOOL**傳回型別和**UINT**和**BOOL\* **參數。 函式應該將參數設定為**TRUE**允許要變更的屬性和**FALSE**不允許。 函式應傳回**TRUE**表示通知已處理，否則**FALSE**。  
  
 `pfnChanged`  
 處理成員函式指標**OnChanged**通知，此屬性。 函式應該具有**BOOL**傳回型別和**UINT**參數。 函式應傳回**TRUE**表示通知已處理，否則**FALSE**。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdisp.h  
  
##  <a name="on_propnotify_reflect"></a>ON_PROPNOTIFY_REFLECT  
 `ON_PROPNOTIFY_REFLECT`巨集，使用在事件接收對應的 OLE 控制項的包裝函式類別時，接收控制項的容器處理前，由控制項傳送的屬性通知。  
  
```  
 
ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 這個事件接收對應所屬的類別。  
  
 `dispid`  
 參與通知屬性的分派 ID。  
  
 `pfnRequest`  
 處理成員函式指標**OnRequestEdit**通知，此屬性。 此函式應該具有**BOOL**傳回型別和**BOOL\* **參數。 此函式應該將參數設定為**TRUE**允許要變更的屬性和**FALSE**不允許。 函式應傳回**TRUE**表示通知已處理，否則**FALSE**。  
  
 `pfnChanged`  
 處理成員函式指標**OnChanged**通知，此屬性。 函式應該具有**BOOL**傳回型別和任何參數。 函式應傳回**TRUE**表示通知已處理，否則**FALSE**。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdisp.h  
    
## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)

