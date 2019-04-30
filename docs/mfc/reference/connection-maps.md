---
title: 連接對應
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.maps
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
ms.openlocfilehash: cbd993e7172ca9a25f25db18d5d0fa042db847b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62373293"
---
# <a name="connection-maps"></a>連接對應

OLE 控制項可將介面公開給其他應用程式。 這些介面只允許從容器的存取權，至該控制項。 如果 OLE 控制項要存取的其他 OLE 物件的外部介面時，就必須建立連接點。 這個連接點可讓連出外部的分派對應，例如事件對應或通知函式的存取控制。

Microsoft Foundation Class Library 會提供支援的連接點的程式設計模型。 在此模型中，「 連接對應 」 用來指派介面或 OLE 控制項的連接點。 連接對應包含一個巨集，每個連接點。 如需有關連接對應的詳細資訊，請參閱[CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md)類別。

一般而言，控制項將會支援兩個連接點： 一個用於事件，其中的屬性通知。 藉由實作這些`COleControl`基底類別，而需要控制寫入器沒有其他工作。 您想要在類別中實作的任何其他連接點必須以手動方式新增。 若要支援連接對應和點，MFC 提供下列巨集：

### <a name="connection-map-declaration-and-demarcation"></a>連接對應宣告和區分

|||
|-|-|
|[BEGIN_CONNECTION_PART](#begin_connection_part)|宣告內嵌的類別實作 （必須使用類別宣告中） 的其他連接點。|
|[END_CONNECTION_PART](#end_connection_part)|宣告的結尾 （必須使用類別宣告中） 的連接點。|
|[CONNECTION_IID](#connection_iid)|指定控制項的連接點的介面 ID。|
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|宣告連接對應將用於 （必須使用類別宣告中） 的類別。|
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|開始連接對應 （必須使用在類別實作） 的定義。|
|[END_CONNECTION_MAP](#end_connection_map)|結束連接對應 （必須使用在類別實作） 的定義。|
|[CONNECTION_PART](#connection_part)|在控制項的連線對應中指定的連接點。|

下列功能協助建立與中斷連接使用的連接點的連線接收：

### <a name="initializationtermination-of-connection-points"></a>初始化/終止的連接點

|||
|-|-|
|[AfxConnectionAdvise](#afxconnectionadvise)|建立來源和接收器之間的連線。|
|[AfxConnectionUnadvise](#afxconnectionunadvise)|中斷來源和接收器之間的連線。|

##  <a name="begin_connection_part"></a>  BEGIN_CONNECTION_PART

若要開始的事件和屬性的告知連接點以外的其他連接點定義使用 BEGIN_CONNECTION_PART 巨集。

```
BEGIN_CONNECTION_PART(theClass, localClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
指定的連接點這個控制項類別的名稱。

*localClass*<br/>
指定實作連接點之區域類別的名稱。

### <a name="remarks"></a>備註

在定義您的類別成員函式宣告 (.h) 檔案中，開始 BEGIN_CONNECTION_PART 巨集的連接點，然後新增 CONNECTION_IID 巨集和您想要實作，任何其他成員函式並完成連線END_CONNECTION_PART 巨集的點對應。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h

##  <a name="end_connection_part"></a>  END_CONNECTION_PART

結束連接點的宣告。

```
END_CONNECTION_PART(localClass)
```

### <a name="parameters"></a>參數

*localClass*<br/>
指定實作連接點之區域類別的名稱。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h

##  <a name="connection_iid"></a>  CONNECTION_IID

使用 BEGIN_CONNECTION_PART 之間 END_CONNECTION_PART 巨集來定義 OLE 控制項所支援的連接點的介面識別碼。

```
CONNECTION_IID(iid)
```

### <a name="parameters"></a>參數

*iid*<br/>
連接點所呼叫介面的介面 ID。

### <a name="remarks"></a>備註

*Iid*引數是用來識別連接點會在其連接的接收器呼叫的介面識別碼的介面。 例如：

[!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]

指定呼叫 `ISinkInterface` 介面的連接點。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h

##  <a name="declare_connection_map"></a>  DECLARE_CONNECTION_MAP

程式中的每個 `COleControl` 衍生類別都可以提供一個連接對應，用於指定您的控制項所支援的其他連接點。

```
DECLARE_CONNECTION_MAP()
```

### <a name="remarks"></a>備註

如果您的控制項支援額外的點，請在類別宣告的結尾使用 DECLARE_CONNECTION_MAP 巨集。 接著，在定義類別的成員函式的.cpp 檔案，使用 BEGIN_CONNECTION_MAP 巨集、 CONNECTION_PART 巨集，每個控制項的連接點和 END_CONNECTION_MAP 巨集來宣告連接對應的結尾。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h

##  <a name="begin_connection_map"></a>  BEGIN_CONNECTION_MAP

程式中每個 `COleControl` 衍生類別可以提供連接對應，以指定控制項支援的連接點。

```
BEGIN_CONNECTION_MAP(theClass, theBase)
```

### <a name="parameters"></a>參數

*theClass*<br/>
指定連接對應之控制項類別的名稱。

*theBase*<br/>
指定的基底類別的名稱*theClass*。

### <a name="remarks"></a>備註

在實作 (。CPP) 檔案，可定義成員函式類別，BEGIN_CONNECTION_MAP 巨集啟動連接對應，然後針對每一個您使用的連接點加入巨集項目[CONNECTION_PART](#connection_part)巨集。 最後，完成連接對應，與[END_CONNECTION_MAP](#end_connection_map)巨集。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h

##  <a name="end_connection_map"></a>  END_CONNECTION_MAP

結束連接對應的定義。

```
END_CONNECTION_MAP()
```

### <a name="requirements"></a>需求

  **標頭**afxdisp.h

##  <a name="connection_part"></a>  CONNECTION_PART

將您的 OLE 控制項的連接點對應到特定的介面識別碼。

```
CONNECTION_PART(theClass, iid, localClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
指定的連接點這個控制項類別的名稱。

*iid*<br/>
連接點所呼叫介面的介面 ID。

*localClass*<br/>
指定實作連接點之區域類別的名稱。

### <a name="remarks"></a>備註

例如: 

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]

實作連接對應，與連接點，呼叫`IID_ISinkInterface`介面。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h

##  <a name="afxconnectionadvise"></a>  AfxConnectionAdvise

呼叫此函式，以建立所指定的來源之間的連線*pUnkSrc*，和所指定的接收器*pUnkSink*。

```
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD FAR* pdwCookie);
```

### <a name="parameters"></a>參數

*pUnkSrc*<br/>
呼叫介面的物件指標。

*pUnkSink*<br/>
實作介面的物件指標。

*iid*<br/>
連接的介面識別碼。

*bRefCount*<br/>
TRUE 表示建立的連線應該會造成參考計數*pUnkSink*遞增。 FALSE 表示不應該遞增參考計數。

*pdwCookie*<br/>
Dword，其中傳回的連線識別碼的指標。 此值應該傳遞為*dwCookie*參數來`AfxConnectionUnadvise`時中斷連線的連線。

### <a name="return-value"></a>傳回值

非零值，如果已建立連線;否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]

### <a name="requirements"></a>需求

**標頭：** afxctl.h

##  <a name="afxconnectionunadvise"></a>  AfxConnectionUnadvise

呼叫此函式，若要中斷連線，以指定的來源之間*pUnkSrc*，和所指定的接收器*pUnkSink*。

```
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD dwCookie);
```

### <a name="parameters"></a>參數

*pUnkSrc*<br/>
呼叫介面的物件指標。

*pUnkSink*<br/>
實作介面的物件指標。

*iid*<br/>
連接點介面的介面識別碼。

*bRefCount*<br/>
TRUE 表示中斷連線的連線應該會造成參考計數*pUnkSink*遞減。 FALSE 表示不應遞減參考計數。

*dwCookie*<br/>
所傳回的連接識別碼`AfxConnectionAdvise`。

### <a name="return-value"></a>傳回值

非零值，如果連線已中斷連線;否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]

### <a name="requirements"></a>需求

**標頭：** afxctl.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
