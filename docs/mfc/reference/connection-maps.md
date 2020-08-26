---
title: 連接對應
ms.date: 11/04/2016
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
ms.openlocfilehash: 517017e9e60b86e96daa24f7822538e91c609fb4
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841411"
---
# <a name="connection-maps"></a>連接對應

OLE 控制項能夠將介面公開給其他應用程式。 這些介面僅允許從容器到該控制項的存取。 如果 OLE 控制項想要存取其他 OLE 物件的外部介面，則必須建立連接點。 此連接點可讓您控制外部分派對應的傳出存取，例如事件對應或通知功能。

MFC 程式庫提供支援連接點的程式設計模型。 在此模型中，會使用「連接對應」來指定 OLE 控制項的介面或連接點。 連接對應包含每個連接點的一個宏。 如需連接對應的詳細資訊，請參閱 [CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md) 類別。

控制項通常只會支援兩個連接點：一個用於事件，一個用於屬性通知。 這些是由基類所執行 `COleControl` ，而且控制項寫入器不需要額外的工作。 您要在類別中執行的任何其他連接點都必須手動新增。 為了支援連接對應和點，MFC 提供下列宏：

### <a name="connection-map-declaration-and-demarcation"></a>連接對應宣告和分界

|名稱|描述|
|-|-|
|[BEGIN_CONNECTION_PART](#begin_connection_part)|宣告實 (必須在類別宣告) 中使用之其他連接點的內嵌類別。|
|[END_CONNECTION_PART](#end_connection_part)|結束連接點的宣告 (必須在類別宣告) 中使用。|
|[CONNECTION_IID](#connection_iid)|指定控制項連接點的介面識別碼。|
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|宣告要在類別中使用的連接對應 (必須在類別宣告) 中使用。|
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|開始 (必須在類別實) 中使用連接對應的定義。|
|[END_CONNECTION_MAP](#end_connection_map)|結束連接對應的定義 (必須在類別實) 中使用。|
|[CONNECTION_PART](#connection_part)|在控制項的連接對應中指定連接點。|

下列函式會協助接收器使用連接點建立和中斷連接：

### <a name="initializationtermination-of-connection-points"></a>連接點的初始化/終止

|名稱|描述|
|-|-|
|[AfxConnectionAdvise](#afxconnectionadvise)|建立來源和接收之間的連接。|
|[AfxConnectionUnadvise](#afxconnectionunadvise)|中斷來源與接收之間的連接。|

## <a name="begin_connection_part"></a><a name="begin_connection_part"></a> BEGIN_CONNECTION_PART

使用 BEGIN_CONNECTION_PART 宏來開始定義事件和屬性通知連接點以外的其他連接點。

```
BEGIN_CONNECTION_PART(theClass, localClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
指定連接點所屬的控制項類別名稱。

*localClass*<br/>
指定實作連接點之區域類別的名稱。

### <a name="remarks"></a>備註

在定義類別成員函式的宣告 ( .h) 檔案中，使用 BEGIN_CONNECTION_PART 宏來啟動連接點，然後新增 CONNECTION_IID 宏和您想要執行的任何其他成員函式，並使用 END_CONNECTION_PART 宏來完成連接點對應。

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="end_connection_part"></a><a name="end_connection_part"></a> END_CONNECTION_PART

結束連接點的宣告。

```
END_CONNECTION_PART(localClass)
```

### <a name="parameters"></a>參數

*localClass*<br/>
指定實作連接點之區域類別的名稱。

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="connection_iid"></a><a name="connection_iid"></a> CONNECTION_IID

在 BEGIN_CONNECTION_PART 和 END_CONNECTION_PART 宏之間使用，為您的 OLE 控制項所支援的連接點定義介面識別碼。

```
CONNECTION_IID(iid)
```

### <a name="parameters"></a>參數

*Iid*<br/>
連接點所呼叫介面的介面 ID。

### <a name="remarks"></a>備註

*Iid*引數是用來識別連接點將在其連接的接收上呼叫之介面的介面識別碼。 例如：

[!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]

指定呼叫 `ISinkInterface` 介面的連接點。

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="declare_connection_map"></a><a name="declare_connection_map"></a> DECLARE_CONNECTION_MAP

程式中的每個 `COleControl` 衍生類別都可以提供一個連接對應，用於指定您的控制項所支援的其他連接點。

```
DECLARE_CONNECTION_MAP()
```

### <a name="remarks"></a>備註

如果您的控制項支援其他點，請在類別宣告的結尾使用 DECLARE_CONNECTION_MAP 宏。 然後，在定義類別成員函式的 .cpp 檔案中，使用 BEGIN_CONNECTION_MAP 宏，CONNECTION_PART 每個控制項連接點的宏，以及 END_CONNECTION_MAP 宏來宣告連接對應的結尾。

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="begin_connection_map"></a><a name="begin_connection_map"></a> BEGIN_CONNECTION_MAP

程式中每個 `COleControl` 衍生類別可以提供連接對應，以指定控制項支援的連接點。

```
BEGIN_CONNECTION_MAP(theClass, theBase)
```

### <a name="parameters"></a>參數

*theClass*<br/>
指定連接對應之控制項類別的名稱。

*theBase*<br/>
指定 *theClass*基類的名稱。

### <a name="remarks"></a>備註

在 [執行 (] 中。為您的類別定義成員函式的 CPP) 檔案、使用 BEGIN_CONNECTION_MAP 宏啟動連接對應，然後使用 [CONNECTION_PART](#connection_part) 宏為每個連接點加入宏專案。 最後，使用 [END_CONNECTION_MAP](#end_connection_map) 宏完成連接對應。

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="end_connection_map"></a><a name="end_connection_map"></a> END_CONNECTION_MAP

結束連接對應的定義。

```
END_CONNECTION_MAP()
```

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="connection_part"></a><a name="connection_part"></a> CONNECTION_PART

將 OLE 控制項的連接點對應至特定的介面識別碼。

```
CONNECTION_PART(theClass, iid, localClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
指定連接點所屬的控制項類別名稱。

*Iid*<br/>
連接點所呼叫介面的介面 ID。

*localClass*<br/>
指定實作連接點之區域類別的名稱。

### <a name="remarks"></a>備註

例如：

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]

使用連接點來執行連接對應，以呼叫 `IID_ISinkInterface` 介面。

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="afxconnectionadvise"></a><a name="afxconnectionadvise"></a> AfxConnectionAdvise

呼叫此函式，以建立由 *pUnkSrc*指定的來源與 *pUnkSink*所指定之接收之間的連接。

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
呼叫介面之物件的指標。

*pUnkSink*<br/>
執行介面之物件的指標。

*Iid*<br/>
連接的介面識別碼。

*bRefCount*<br/>
TRUE 表示建立連接應該會使 *pUnkSink* 的參考計數遞增。 FALSE 表示參考計數不應遞增。

*pdwCookie*<br/>
DWORD 的指標，其中會傳回連接識別碼。 *dwCookie* `AfxConnectionUnadvise` 當中斷連接連接時，應該將此值當作 dwCookie 參數傳遞給。

### <a name="return-value"></a>傳回值

如果已建立連接，則為非零;否則為0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afxctl.h。h

## <a name="afxconnectionunadvise"></a><a name="afxconnectionunadvise"></a> AfxConnectionUnadvise

呼叫此函式可中斷來源（由 *pUnkSrc*指定）與接收（由 *pUnkSink*指定）之間的連接。

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
呼叫介面之物件的指標。

*pUnkSink*<br/>
執行介面之物件的指標。

*Iid*<br/>
連接點介面的介面識別碼。

*bRefCount*<br/>
TRUE 表示中斷連接連接應該會減少 *pUnkSink* 的參考計數。 FALSE 表示不應遞減參考計數。

*dwCookie*<br/>
所傳回的連接識別碼 `AfxConnectionAdvise` 。

### <a name="return-value"></a>傳回值

如果連接中斷，則為非零;否則為0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afxctl.h。h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
