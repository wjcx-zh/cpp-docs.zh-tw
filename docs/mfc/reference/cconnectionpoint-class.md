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
ms.openlocfilehash: ce72c156ab31b742a42d2960923fc56afff656c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369434"
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
|[連接點:C 連接點](#cconnectionpoint)|建構 `CConnectionPoint` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 連接點:抓取連線](#getconnections)|檢索連接映射中的所有連接點。|
|[C 連接點:抓取容器](#getcontainer)|檢索擁有連接映射的控制件的容器。|
|[連接點:取得 IID](#getiid)|檢索連接點的介面 ID。|
|[連接點::取得最大連線](#getmaxconnections)|檢索控制項支援的最大連接點數。|
|[C 連接點::取得下一個連線](#getnextconnection)|檢索指向*pos*處的連接元素的指標。|
|[連接點::抓取起始位置](#getstartposition)|通過返回可以傳遞給`GetNextConnection`調用的定位值來啟動映射反覆運算。|
|[連接點::上建議](#onadvise)|建立或斷開連接時由框架調用。|
|[連接點::查詢Sink介面](#querysinkinterface)|檢索指向請求的接收器介面的指標。|

## <a name="remarks"></a>備註

與用於實現和公開 OLE 控制元件功能的正常 OLE 介面不同,連接點實現了一個傳出介面,該介面能夠對其他物件(如觸發事件和更改通知)啟動操作。

連接由兩部分組成:調用介面的物件稱為"源",實現介面的對象稱為"接收器"。 通過公開連接點,源允許接收器建立與自身的連接。 通過連接點機制,源物件獲取指向接收器實現一組成員函數的指標。 例如,要觸發由接收器實現的事件,源可以調用接收器實現的適當方法。

預設情況下,`COleControl`派生類實現兩個連接點:一個用於事件,一個用於屬性更改通知。 這些連接分別用於事件觸發和屬性值更改時通知接收器(例如控制項的容器)。 還支援 OLE 控制件實現其他連接點。 對於在控制類中實現的每個附加連接點,必須聲明實現連接點的"連接部件"。 如果實現一個或多個連接點,還需要在控制類中聲明單個"連接映射"。

下面的範例演示了`Sample`OLE 控制項的簡單連接映射和一個連接點,由兩個程式碼片段組成:第一部分聲明連接映射和點;第二部分聲明連接映射和點;第二部分聲明連接映射和點。第二個實現此映射和點。 第一個片段插入到控制類的聲明中,在**受保護的**部分下:

[!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]

BEGIN_CONNECTION_PART宏和END_CONNECTION_PART宏聲明實現此特定連接點的`XSampleConnPt`嵌入式類`CConnectionPoint`( 派生自 )。 如果要重寫任何`CConnectionPoint`成員函數,或添加您自己的成員函數,請在這兩個宏之間聲明它們。 例如,CONNECTION_IID宏在這兩個宏之間`CConnectionPoint::GetIID`放置時將覆蓋成員函數。

第二個程式碼片段插入到實現檔 (。控制類的 CPP)。 此代碼實現連接映射,其中包括其他連接點: `SampleConnPt`

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]

插入這些程式片段後,範例 OLE 控制項將公開介面`ISampleSink`的連接點。

通常,連接點支援"多播",即廣播到連接到同一介面的多個接收器的能力。 以下片段的簡用如何透過連接點上的每個接收器的發運算來實現多播:

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

這個範例取得連接`SampleConnPt`點上的目前連線集,並呼叫`CConnectionPoint::GetConnections`。 然後,它通過連接進行遍接,並調用`ISampleSink::SinkFunc`每個活動連接。

有關`CConnectionPoint`使用的詳細資訊,請參考文章[連接點](../../mfc/connection-points.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CConnectionPoint`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="cconnectionpointcconnectionpoint"></a><a name="cconnectionpoint"></a>連接點:C 連接點

建構 `CConnectionPoint` 物件。

```
CConnectionPoint();
```

## <a name="cconnectionpointgetconnections"></a><a name="getconnections"></a>C 連接點:抓取連線

調用此函數以檢索連接點的所有活動連接。

```
const CPtrArray* GetConnections();
```

### <a name="return-value"></a>傳回值

指向活動連接(接收器)陣列的指標。 陣列中的某些指標可能為 NULL。 此陣列中的每個非 NULL 指標都可以使用強制轉換運算符安全地轉換為到接收器介面的指標。

## <a name="cconnectionpointgetcontainer"></a><a name="getcontainer"></a>C 連接點:抓取容器

由框架調用以檢索`IConnectionPointContainer`連接點。

```
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```

### <a name="return-value"></a>傳回值

如果成功,則指向容器的指標;否則 NULL。

### <a name="remarks"></a>備註

此函數通常由BEGIN_CONNECTION_PART宏實現。

## <a name="cconnectionpointgetiid"></a><a name="getiid"></a>連接點:取得 IID

由框架調用以檢索連接點的介面 ID。

```
virtual REFIID GetIID() = 0;
```

### <a name="return-value"></a>傳回值

對連接點介面 ID 的引用。

### <a name="remarks"></a>備註

重寫此函數以返回此連接點的介面 ID。

## <a name="cconnectionpointgetmaxconnections"></a><a name="getmaxconnections"></a>連接點::取得最大連線

由框架調用以檢索連接點支援的最大連接數。

```
virtual int GetMaxConnections();
```

### <a name="return-value"></a>傳回值

控制項支援的最大連接數,如果沒有限制,則為 -1。

### <a name="remarks"></a>備註

默認實現返回 -1,表示沒有限制。

如果要限制可連接到控制項的接收器數,請覆蓋此函數。

## <a name="cconnectionpointgetnextconnection"></a><a name="getnextconnection"></a>C 連接點::取得下一個連線

檢索指向*pos*處的連接元素的指標。

```
LPUNKNOWN GetNextConnection(POSITION& pos) const;
```

### <a name="parameters"></a>參數

*Pos*<br/>
指定對上一次`GetNextConnection`或[GetStart 定位](#getstartposition)呼叫傳回的定位值的引用。

### <a name="return-value"></a>傳回值

指向*pos*指定的連接元素的指標 , 或 NULL。

### <a name="remarks"></a>備註

此功能對於反覆運算連接映射中的所有元素最有用。 反覆運算時,跳過從此功能返回的任何 NUL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

## <a name="cconnectionpointgetstartposition"></a><a name="getstartposition"></a>連接點::抓取起始位置

通過返回可以傳遞到[GetNextConnect](#getnextconnection)調用的定位值來啟動地圖反覆運算。

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>傳回值

指示反覆運算地圖的起始位置的定位值;如果地圖為空,則為 NULL。

### <a name="remarks"></a>備註

反覆運算序列是不可預測的;因此,「地圖中的第一個元素」沒有特殊的意義。

### <a name="example"></a>範例

  請參考[CConnectionPoint 的範例:抓取Next連線](#getnextconnection)。

## <a name="cconnectionpointonadvise"></a><a name="onadvise"></a>連接點::上建議

當建立或斷開連接時由框架調用。

```
virtual void OnAdvise(BOOL bAdvise);
```

### <a name="parameters"></a>參數

*b 建議*<br/>
TRUE,如果正在建立連接;否則 FALSE。

### <a name="remarks"></a>備註

預設實作不做任何動作。

如果要在接收器連接到連接點或斷開連接點時發出通知,請覆蓋此函數。

## <a name="cconnectionpointquerysinkinterface"></a><a name="querysinkinterface"></a>連接點::查詢Sink介面

檢索指向請求的接收器介面的指標。

```
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,
    void** ppInterface);
```

### <a name="parameters"></a>參數

*pUnkSink*<br/>
要請求的接收器介面的標識符。

*ppInterface*<br/>
指向*pUnkSink*標識的介面指標的指標。 如果物件不支援此介面,\**則 ppInterface*設定為 NULL。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
