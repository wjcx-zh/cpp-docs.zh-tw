---
title: "CConnectionPoint 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CConnectionPoint
- AFXDISP/CConnectionPoint
- AFXDISP/CConnectionPoint::CConnectionPoint
- AFXDISP/CConnectionPoint::GetConnections
- AFXDISP/CConnectionPoint::GetContainer
- AFXDISP/CConnectionPoint::GetIID
- AFXDISP/CConnectionPoint::GetMaxConnections
- AFXDISP/CConnectionPoint::GetNextConnection
- AFXDISP/CConnectionPoint::GetStartPosition
- AFXDISP/CConnectionPoint::OnAdvise
- AFXDISP/CConnectionPoint::QuerySinkInterface
dev_langs:
- C++
helpviewer_keywords:
- CConnectionPoint class
ms.assetid: f0f23a1e-5e8c-41a9-aa6c-1a4793b28e8f
caps.latest.revision: 20
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a511f252bf921433d070059518e6e67b952680eb
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cconnectionpoint-class"></a>CConnectionPoint 類別
定義用來與其他 OLE 物件通訊的特殊介面類型，稱為「連接點」。  
  
## <a name="syntax"></a>語法  
  
```  
class CConnectionPoint : public CCmdTarget  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CConnectionPoint::CConnectionPoint](#cconnectionpoint)|建構 `CConnectionPoint` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CConnectionPoint::GetConnections](#getconnections)|擷取所有連線對應的連接點。|  
|[CConnectionPoint::GetContainer](#getcontainer)|擷取擁有連接對應之控制項的容器。|  
|[CConnectionPoint::GetIID](#getiid)|擷取的連接點的介面 ID。|  
|[CConnectionPoint::GetMaxConnections](#getmaxconnections)|擷取控制項所支援的連接點的數目上限。|  
|[CConnectionPoint::GetNextConnection](#getnextconnection)|擷取到連接項目的指標`pos`。|  
|[CConnectionPoint::GetStartPosition](#getstartposition)|一開始會傳回對應的反覆項目**位置**值傳遞至`GetNextConnection`呼叫。|  
|[CConnectionPoint::OnAdvise](#onadvise)|當建立階層或中斷連線的架構所呼叫。|  
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|擷取要求的接收器介面的指標。|  
  
## <a name="remarks"></a>備註  
 不同於一般 OLE 介面，用來實作和公開 OLE 控制項的功能，連接點實作能夠對其他物件，例如引發事件起始動作和變更通知的輸出介面。  
  
 連線包含兩個部分︰ 呼叫的介面，稱為 「 來源 」，以及實作介面之物件的物件呼叫 「 接收 」。 藉由公開連接點，source 可讓接收來建立自己的連接。 連接點機制，透過來源物件會取得接收實作的一組成員函式的指標。 比方說，若要引發事件接收所實作，來源可以呼叫接收實作的適當方法。  
  
 根據預設， `COleControl`-衍生的類別會實作兩個連接點︰ 一個事件，另一個屬性變更通知。 使用這些連線，分別引發事件和通知的接收 （例如，控制項的容器），當屬性值已變更。 若要實作的其他連接點的 OLE 控制項也提供支援。 控制項類別中實作每個額外的連接點，您必須宣告 」 的連接部分 」 實作連接點。 如果您實作一個或多個連接點，您也要宣告單一控制項類別中的 「 連線對應 」。  
  
 下列範例將示範簡單的連接對應，以及一個連接點`Sample`OLE 控制項，其中包含兩個的程式碼片段︰ 第一個部分宣告連接對應和點; 第二個會實作這個對應和點。 在第一個片段插入至控制項類別中，宣告`protected`區段︰  
  
 [!code-cpp[NVC_MFCConnectionPoints #&7;](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]  
  
 `BEGIN_CONNECTION_PART`和`END_CONNECTION_PART`巨集宣告內嵌的類別， `XSampleConnPt` (衍生自`CConnectionPoint`) 來實作這個特定的連接點。 如果您想要覆寫任何`CConnectionPoint`成員函式，或加入您自己的成員函式，將它們宣告這些兩個巨集之間。 例如，`CONNECTION_IID`巨集覆寫`CConnectionPoint::GetIID`成員函式時這些兩個巨集之間。  
  
 第二個程式碼片段插入至實作檔案 (。CPP) 您的控制項類別。 此程式碼實作連接對應，其中包括額外的連接點， `SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints #&2;](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]  
  
 一旦插入下列程式碼片段，範例 OLE 控制項公開 （expose) 的連接點**ISampleSink**介面。  
  
 一般而言，連接點支援 「 多點傳送 」，也就是廣播至多個接收連線到相同的介面。 下列程式碼片段示範如何逐一查看每個接收連接點上多點傳送來完成︰  
  
 [!code-cpp[NVC_MFCConnectionPoints #&4;](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]  
  
 此範例會擷取目前的一組連接上`SampleConnPt`連接點，藉由呼叫`CConnectionPoint::GetConnections`。 它接著會逐一連接並呼叫`ISampleSink::SinkFunc`上每個作用中連線。  
  
 如需有關使用`CConnectionPoint`，請參閱文章[連接點](../../mfc/connection-points.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CConnectionPoint`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdisp.h  
  
##  <a name="cconnectionpoint"></a>CConnectionPoint::CConnectionPoint  
 建構 `CConnectionPoint` 物件。  
  
```  
CConnectionPoint();
```  
  
##  <a name="getconnections"></a>CConnectionPoint::GetConnections  
 呼叫此函式可擷取所有使用中連接的連接點。  
  
```  
const CPtrArray* GetConnections();
```  
  
### <a name="return-value"></a>傳回值  
 作用中連線 （接收） 的陣列指標。 有些陣列中的指標可以是 NULL。 這個陣列中的每個非 NULL 指標可以安全地轉換為使用轉換運算子的接收器介面的指標。  
  
##  <a name="getcontainer"></a>CConnectionPoint::GetContainer  
 要擷取架構呼叫**IConnectionPointContainer**連接點。  
  
```  
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功的話，容器; 的指標否則**NULL**。  
  
### <a name="remarks"></a>備註  
 此函式通常由實作`BEGIN_CONNECTION_PART`巨集。  
  
##  <a name="getiid"></a>CConnectionPoint::GetIID  
 若要擷取的連接點的介面 ID 架構呼叫。  
  
```  
virtual REFIID GetIID() = 0;  
```  
  
### <a name="return-value"></a>傳回值  
 參考的連接點的介面識別碼。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式來傳回這個連接點的介面識別碼。  
  
##  <a name="getmaxconnections"></a>CConnectionPoint::GetMaxConnections  
 若要擷取的連接點所支援的連線數目上限架構呼叫。  
  
```  
virtual int GetMaxConnections();
```  
  
### <a name="return-value"></a>傳回值  
 支援的控制項，則為-1，如果沒有限制的連線數目上限。  
  
### <a name="remarks"></a>備註  
 預設實作會傳回-1，表示沒有限制。  
  
 如果您想要限制接收可連接到您的控制項數目，請覆寫這個函式。  
  
##  <a name="getnextconnection"></a>CConnectionPoint::GetNextConnection  
 擷取到連接項目的指標`pos`。  
  
```  
LPUNKNOWN GetNextConnection(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 指定的參考**位置**前一個傳回值`GetNextConnection`或[GetStartPosition](#getstartposition)呼叫。  
  
### <a name="return-value"></a>傳回值  
 指定的連接元素的指標`pos`，則為 NULL。  
  
### <a name="remarks"></a>備註  
 此函式是最適合用來逐一查看所有連線對應的項目。 時，略過任何從此函數傳回的 null 值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCConnectionPoints #&4;](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]  
  
##  <a name="getstartposition"></a>CConnectionPoint::GetStartPosition  
 一開始會傳回對應的反覆項目**位置**值傳遞至[GetNextConnection](#getnextconnection)呼叫。  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A**位置**值，指出對應; 上逐一查看的開始位置或**NULL**如果對應是空的。  
  
### <a name="remarks"></a>備註  
 反覆項目序列不是可預測的因此，「 第一個項目在對應中的 」 有任何特殊意義。  
  
### <a name="example"></a>範例  
  請參閱範例[CConnectionPoint::GetNextConnection](#getnextconnection)。  
  
##  <a name="onadvise"></a>CConnectionPoint::OnAdvise  
 架構的連線時所呼叫，是建立或中斷。  
  
```  
virtual void OnAdvise(BOOL bAdvise);
```  
  
### <a name="parameters"></a>參數  
 `bAdvise`  
 **TRUE**，如果連接正在建立; 否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 預設實作不做任何動作。  
  
 如果您要通知接收到連接或中斷連接點時，覆寫這個函式。  
  
##  <a name="querysinkinterface"></a>CConnectionPoint::QuerySinkInterface  
 擷取要求的接收器介面的指標。  
  
```  
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,  
    void** ppInterface);
```  
  
### <a name="parameters"></a>參數  
 `pUnkSink`  
 所要求的接收器介面識別碼。  
  
 `ppInterface`  
 所識別的介面指標的指標`pUnkSink`。 如果物件不支援這個介面， \* `ppInterface`設為**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
## <a name="see-also"></a>另請參閱  
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)


