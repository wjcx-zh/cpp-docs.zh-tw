---
title: CConnectionPoint 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- CConnectionPoint [MFC], CConnectionPoint
- CConnectionPoint [MFC], GetConnections
- CConnectionPoint [MFC], GetContainer
- CConnectionPoint [MFC], GetIID
- CConnectionPoint [MFC], GetMaxConnections
- CConnectionPoint [MFC], GetNextConnection
- CConnectionPoint [MFC], GetStartPosition
- CConnectionPoint [MFC], OnAdvise
- CConnectionPoint [MFC], QuerySinkInterface
ms.assetid: f0f23a1e-5e8c-41a9-aa6c-1a4793b28e8f
ms.openlocfilehash: efa8a7bf9e14bd93682fcc2d5802a84f1bdb1e96
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629927"
---
# <a name="cconnectionpoint-class"></a>CConnectionPoint 類別

定義用來與其他 OLE 物件通訊的特殊介面類型，稱為「連接點」。

## <a name="syntax"></a>語法

```
class CConnectionPoint : public CCmdTarget
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CConnectionPoint::CConnectionPoint](#cconnectionpoint)|建構 `CConnectionPoint` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CConnectionPoint::GetConnections](#getconnections)|擷取連接對應中的所有連接點。|
|[CConnectionPoint::GetContainer](#getcontainer)|擷取擁有連接對應之控制項的容器。|
|[CConnectionPoint::GetIID](#getiid)|擷取連接點的介面 ID。|
|[CConnectionPoint::GetMaxConnections](#getmaxconnections)|擷取控制項所支援的連接點的最大數目。|
|[CConnectionPoint::GetNextConnection](#getnextconnection)|擷取連線項目在指標*pos*。|
|[CConnectionPoint::GetStartPosition](#getstartposition)|對應的反覆項目一開始會傳回位置的值可以傳遞至`GetNextConnection`呼叫。|
|[CConnectionPoint::OnAdvise](#onadvise)|由架構建立或中斷連線時呼叫。|
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|擷取要求的接收介面的指標。|

## <a name="remarks"></a>備註

不同於一般的 OLE 介面，用來實作，並公開 （expose） 的 OLE 控制項的功能，連接點會實作可以起始對其他物件，例如引發事件的動作，並變更通知的輸出介面。

連接是由兩個部分所組成： 呼叫的介面，稱為 「 來源 」，以及實作介面之物件的物件呼叫 「 接收 」。 藉由公開的連接點，來源會允許來建立連接至其本身的接收器。 連接點機制，透過來源物件會取得接收實作的一組成員函式的指標。 比方說，若要引發事件接收實作，來源可以呼叫的接收器實作適當的方法。

根據預設， `COleControl`-衍生的類別會實作兩個連接點： 一個事件，另一個屬性變更通知。 使用這些連線，分別針對事件的引發和何時通知 （例如，控制項的容器） 中的接收屬性值已變更。 若要實作的其他連接點的 OLE 控制項也提供支援。 針對每個控制項類別中實作的其他連接點，您必須宣告 「 連接部分 」 實作連接點。 如果您實作一個或多個連接點時，您也需要宣告單一控制項類別中的 「 連接對應 」。

下列範例示範簡單的連接對應，以及一個連接點`Sample`OLE 控制項，其中包含兩個片段的程式碼： 第一個部分宣告連接對應和點; 第二個會實作這個對應和點。 第一個片段插入的控制項類別中，宣告底下**保護**區段：

[!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]

BEGIN_CONNECTION_PART 和 END_CONNECTION_PART 巨集宣告內嵌的類別， `XSampleConnPt` (衍生自`CConnectionPoint`) 會實作這個特定的連接點。 如果您想要覆寫任何`CConnectionPoint`成員函式，或加入您自己的成員函式，將它們宣告這些兩個巨集之間。 例如，CONNECTION_IID 巨集覆寫`CConnectionPoint::GetIID`成員函式時這些兩個巨集之間。

第二個程式碼片段插入至實作檔案 (。CPP) 的控制項類別。 此程式碼會實作連接對應，其中包含額外的連接點， `SampleConnPt`:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]

範例 OLE 控制項之後插入下列程式碼片段，公開的連接點`ISampleSink`介面。

一般而言，連接點支援 「 多點傳送 」，也就是能夠連接到相同的介面的多個接收廣播。 下列程式碼片段示範如何逐一查看每個接收連接點上完成 多點傳送：

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

此範例會擷取目前的連線集上`SampleConnPt`藉由呼叫的連接點`CConnectionPoint::GetConnections`。 然後重複執行的連線和呼叫`ISampleSink::SinkFunc`上作用中的每個連接。

如需有關使用`CConnectionPoint`，請參閱文章[連接點](../../mfc/connection-points.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CConnectionPoint`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

##  <a name="cconnectionpoint"></a>  CConnectionPoint::CConnectionPoint

建構 `CConnectionPoint` 物件。

```
CConnectionPoint();
```

##  <a name="getconnections"></a>  CConnectionPoint::GetConnections

呼叫此函式可擷取所有使用中連接的連接點。

```
const CPtrArray* GetConnections();
```

### <a name="return-value"></a>傳回值

作用中連線 （接收） 的陣列指標。 部分中陣列的指標可以是 NULL。 此陣列中的每個非 NULL 指標可以安全地轉換使用 cast 運算子將接收介面的指標。

##  <a name="getcontainer"></a>  CConnectionPoint::GetContainer

由架構呼叫以擷取`IConnectionPointContainer`連接點。

```
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```

### <a name="return-value"></a>傳回值

如果成功，指向容器中;否則為 NULL。

### <a name="remarks"></a>備註

此函式通常是由 BEGIN_CONNECTION_PART 巨集實作。

##  <a name="getiid"></a>  CConnectionPoint::GetIID

由架構呼叫以擷取連接點的介面 ID。

```
virtual REFIID GetIID() = 0;
```

### <a name="return-value"></a>傳回值

參考的連接點的介面 id。

### <a name="remarks"></a>備註

覆寫這個函式來傳回這個連接點的介面識別碼。

##  <a name="getmaxconnections"></a>  CConnectionPoint::GetMaxConnections

由架構呼叫以擷取的連接點所支援的連線數目上限。

```
virtual int GetMaxConnections();
```

### <a name="return-value"></a>傳回值

支援的控制項，則為-1，如果沒有限制連線數目上限。

### <a name="remarks"></a>備註

預設實作會傳回-1，表示沒有任何限制。

如果您想要限制接收可連線到您的控制項數目，請覆寫這個函式。

##  <a name="getnextconnection"></a>  CConnectionPoint::GetNextConnection

擷取連線項目在指標*pos*。

```
LPUNKNOWN GetNextConnection(POSITION& pos) const;
```

### <a name="parameters"></a>參數

*pos*<br/>
指定前一個位置值的參考`GetNextConnection`或是[GetStartPosition](#getstartposition)呼叫。

### <a name="return-value"></a>傳回值

指定的連接元素的指標*pos*，則為 NULL。

### <a name="remarks"></a>備註

此函式是最適合用來逐一查看連線對應中的所有項目。 逐一查看時, 略過此函式所傳回的任何 null 值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

##  <a name="getstartposition"></a>  CConnectionPoint::GetStartPosition

對應的反覆項目一開始會傳回位置的值可以傳遞給[GetNextConnection](#getnextconnection)呼叫。

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>傳回值

位置值，指出逐一查看對應的開始位置或者，如果 map 是空的則為 NULL。

### <a name="remarks"></a>備註

反覆項目序列不是可預測的因此，「 第一個 map 中的元素 「 必須沒有特殊意義。

### <a name="example"></a>範例

  範例，請參閱[CConnectionPoint::GetNextConnection](#getnextconnection)。

##  <a name="onadvise"></a>  CConnectionPoint::OnAdvise

由架構的連線時呼叫，是建立或中斷。

```
virtual void OnAdvise(BOOL bAdvise);
```

### <a name="parameters"></a>參數

*bAdvise*<br/>
為 TRUE，如果正在建立連線;否則為 FALSE。

### <a name="remarks"></a>備註

預設實作不做任何動作。

如果您想要通知，連接到接收，或從您的連接點中斷連線時，請覆寫這個函式。

##  <a name="querysinkinterface"></a>  CConnectionPoint::QuerySinkInterface

擷取要求的接收介面的指標。

```
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,
    void** ppInterface);
```

### <a name="parameters"></a>參數

*pUnkSink*<br/>
接收介面所要求的識別碼。

*ppInterface*<br/>
所識別之介面指標的指標*pUnkSink*。 如果物件不支援這個介面， \* *ppInterface*設為 NULL。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)

