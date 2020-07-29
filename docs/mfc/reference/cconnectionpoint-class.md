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
ms.openlocfilehash: f428ec597e0e4a56788fae2455eff80b286fda39
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87183080"
---
# <a name="cconnectionpoint-class"></a>CConnectionPoint 類別

定義用來與其他 OLE 物件通訊的特殊介面類型，稱為「連接點」。

## <a name="syntax"></a>語法

```
class CConnectionPoint : public CCmdTarget
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CConnectionPoint::CConnectionPoint](#cconnectionpoint)|建構 `CConnectionPoint` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CConnectionPoint::GetConnections](#getconnections)|抓取連接對應中的所有連接點。|
|[CConnectionPoint::GetContainer](#getcontainer)|抓取擁有連接對應之控制項的容器。|
|[CConnectionPoint::GetIID](#getiid)|抓取連接點的介面識別碼。|
|[CConnectionPoint：： GetMaxConnections](#getmaxconnections)|抓取控制項支援的最大連接點數目。|
|[CConnectionPoint::GetNextConnection](#getnextconnection)|抓取位於*pos*之 connection 元素的指標。|
|[CConnectionPoint::GetStartPosition](#getstartposition)|藉由傳回可傳遞至呼叫的位置值來啟動對應反復專案 `GetNextConnection` 。|
|[CConnectionPoint::OnAdvise](#onadvise)|建立或中斷連接時由架構呼叫。|
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|抓取所要求接收介面的指標。|

## <a name="remarks"></a>備註

不同于用來實並公開 OLE 控制項功能的一般 OLE 介面，連接點會執行可對其他物件起始動作（例如引發事件和變更通知）的輸出介面。

連接是由兩個部分組成：呼叫介面的物件，稱為「來源」，而執行介面的物件稱為「接收」。 藉由公開連接點，來源可讓接收與本身建立連接。 透過連接點機制，來源物件會取得一組成員函式的接收的指標。 例如，若要引發接收器所執行的事件，來源可以呼叫接收器的適當方法來執行。

根據預設， `COleControl` 衍生的類別會執行兩個連接點：一個用於事件，另一個用於屬性變更通知。 這些連接分別用於引發事件，以及在屬性值已變更時通知接收器（例如，控制項的容器）。 此外，也提供 OLE 控制項的支援，以執行其他連接點。 針對在控制項類別中所實的每個額外連接點，您必須宣告可執行連接點的「連接元件」。 如果您執行一或多個連接點，您也必須在控制項類別中宣告單一「連接對應」。

下列範例示範一個簡單的連接對應和一個 OLE 控制項的連接點 `Sample` ，其中包含兩個程式碼片段：第一個部分會宣告連接對應和點，第二個部分則會執行這個對應和點。 第一個片段會插入至控制項類別的宣告中，位於區段底下 **`protected`** ：

[!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]

BEGIN_CONNECTION_PART 和 END_CONNECTION_PART 宏會宣告可執行 `XSampleConnPt` `CConnectionPoint` 這個特定連接點的內嵌類別（衍生自）。 如果您想要覆寫任何成員函式 `CConnectionPoint` ，或加入您自己的成員函式，請在這兩個宏之間宣告它們。 例如，在 `CConnectionPoint::GetIID` 這兩個宏之間放置時，CONNECTION_IID 宏會覆寫成員函式。

第二個程式碼片段會插入至執行檔（。CPP）的控制項類別。 此程式碼會執行連接對應，其中包括其他連接點 `SampleConnPt` ：

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]

插入這些程式碼片段之後，範例 OLE 控制項會公開介面的連接點 `ISampleSink` 。

一般而言，連接點支援「多播」，這是廣播到連接到相同介面之多個接收器的能力。 下列程式碼片段示範如何逐一查看連接點上的每個接收來完成多播：

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

這個範例會使用的呼叫，來抓取連接點上目前的連接集 `SampleConnPt` `CConnectionPoint::GetConnections` 。 然後，它會逐一查看連接，並 `ISampleSink::SinkFunc` 在每個使用中的連接上呼叫。

如需有關使用的詳細資訊 `CConnectionPoint` ，請參閱[連接點](../../mfc/connection-points.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CConnectionPoint`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="cconnectionpointcconnectionpoint"></a><a name="cconnectionpoint"></a>CConnectionPoint::CConnectionPoint

建構 `CConnectionPoint` 物件。

```
CConnectionPoint();
```

## <a name="cconnectionpointgetconnections"></a><a name="getconnections"></a>CConnectionPoint::GetConnections

呼叫此函式可取得連接點的所有作用中連接。

```
const CPtrArray* GetConnections();
```

### <a name="return-value"></a>傳回值

作用中連接（接收）陣列的指標。 陣列中的某些指標可能是 Null。 這個陣列中的每個非 Null 指標都可以使用 cast 運算子安全地轉換成接收介面的指標。

## <a name="cconnectionpointgetcontainer"></a><a name="getcontainer"></a>CConnectionPoint::GetContainer

由架構呼叫，以取得 `IConnectionPointContainer` 連接點的。

```
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```

### <a name="return-value"></a>傳回值

如果成功，則為容器的指標;否則為 Null。

### <a name="remarks"></a>備註

此函式通常會由 BEGIN_CONNECTION_PART 宏來執行。

## <a name="cconnectionpointgetiid"></a><a name="getiid"></a>CConnectionPoint::GetIID

由架構呼叫以抓取連接點的介面識別碼。

```
virtual REFIID GetIID() = 0;
```

### <a name="return-value"></a>傳回值

連接點之介面識別碼的參考。

### <a name="remarks"></a>備註

覆寫這個函式，以傳回這個連接點的介面識別碼。

## <a name="cconnectionpointgetmaxconnections"></a><a name="getmaxconnections"></a>CConnectionPoint：： GetMaxConnections

由架構呼叫，以取得連接點所支援的最大連接數目。

```
virtual int GetMaxConnections();
```

### <a name="return-value"></a>傳回值

控制項支援的最大連接數目，如果沒有限制則為-1。

### <a name="remarks"></a>備註

預設的執行會傳回-1，表示沒有限制。

如果您想要限制可以連接到您的控制項的接收數目，請覆寫此函式。

## <a name="cconnectionpointgetnextconnection"></a><a name="getnextconnection"></a>CConnectionPoint::GetNextConnection

抓取位於*pos*之 connection 元素的指標。

```
LPUNKNOWN GetNextConnection(POSITION& pos) const;
```

### <a name="parameters"></a>參數

*採購*<br/>
指定前一個 `GetNextConnection` 或[GetStartPosition](#getstartposition)呼叫所傳回之位置值的參考。

### <a name="return-value"></a>傳回值

*Pos*所指定之 connection 元素的指標，或為 Null。

### <a name="remarks"></a>備註

此函式最適合用於逐一查看連接對應中的所有元素。 反覆運算時，略過此函式所傳回的任何 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

## <a name="cconnectionpointgetstartposition"></a><a name="getstartposition"></a>CConnectionPoint::GetStartPosition

藉由傳回可傳遞至[GetNextConnection](#getnextconnection)呼叫的位置值，來啟動對應反復專案。

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>傳回值

位置值，表示反覆運算對應的開始位置。如果對應是空的，則為 Null。

### <a name="remarks"></a>備註

反復專案序列無法預測;因此，「對應」中的「第一個元素」沒有特殊意義。

### <a name="example"></a>範例

  請參閱[CConnectionPoint：： GetNextConnection](#getnextconnection)的範例。

## <a name="cconnectionpointonadvise"></a><a name="onadvise"></a>CConnectionPoint::OnAdvise

在建立或中斷連接時由架構呼叫。

```
virtual void OnAdvise(BOOL bAdvise);
```

### <a name="parameters"></a>參數

*bAdvise*<br/>
若正在建立連接，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

預設實作不做任何動作。

如果您想要在接收器連接到連接點或中斷連線時發出通知，請覆寫此函式。

## <a name="cconnectionpointquerysinkinterface"></a><a name="querysinkinterface"></a>CConnectionPoint::QuerySinkInterface

抓取所要求接收介面的指標。

```
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,
    void** ppInterface);
```

### <a name="parameters"></a>參數

*pUnkSink*<br/>
所要求之接收介面的識別碼。

*ppInterface*<br/>
*PUnkSink*所識別之介面指標的指標。 如果物件不支援這個介面， \* *ppInterface*會設定為 Null。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
