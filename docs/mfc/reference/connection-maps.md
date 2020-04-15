---
title: 連接對應
ms.date: 11/04/2016
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
ms.openlocfilehash: 947cd09023ef4028a32db8e2e4e8b33f7e04e0dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374795"
---
# <a name="connection-maps"></a>連接對應

OLE 控制項能夠將介面公開給其他應用程式。 這些介面只允許從容器訪問該控制項。 如果 OLE 控制者想要存取其他 OLE 物件的外部介面,則必須建立連接點。 此連接點允許控件向外訪問外部調度映射,如事件映射或通知函數。

Microsoft 基礎類庫提供了支援連接點的程式設計模型。 在此模型中,「連接映射」用於為 OLE 控制件指定介面或連接點。 連接映射包含每個連接點的一個宏。 有關連接映射的詳細資訊,請參閱[CConnectPoint](../../mfc/reference/cconnectionpoint-class.md)類。

通常,控件僅支援兩個連接點:一個用於事件,一個用於屬性通知。 這些由基類實現`COleControl`,不需要控件編寫器的額外工作。 必須在類中實現任何其他連接點都必須手動添加。 為了支援連接映射和點,MFC 提供以下宏:

### <a name="connection-map-declaration-and-demarcation"></a>連接映射宣告和標界

|||
|-|-|
|[BEGIN_CONNECTION_PART](#begin_connection_part)|聲明實現附加連接點的嵌入類(必須在類聲明中使用)。|
|[END_CONNECTION_PART](#end_connection_part)|結束連接點的聲明(必須在類聲明中使用)。|
|[CONNECTION_IID](#connection_iid)|指定控制項連接點的介面 ID。|
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|聲明連接映射將在類中使用(必須在類聲明中使用)。|
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|開始定義連接映射(必須在類實現中使用)。|
|[END_CONNECTION_MAP](#end_connection_map)|結束連接映射的定義(必須在類實現中使用)。|
|[CONNECTION_PART](#connection_part)|在控制項的連接對應中指定連接點。|

以下功能可説明接收器使用連接點建立和斷線連線:

### <a name="initializationtermination-of-connection-points"></a>連接點的初始化/終止

|||
|-|-|
|[AfxConnectionAdvise](#afxconnectionadvise)|在源和接收器之間建立連接。|
|[AfxConnectionUnadvise](#afxconnectionunadvise)|斷開源和接收器之間的連接。|

## <a name="begin_connection_part"></a><a name="begin_connection_part"></a>BEGIN_CONNECTION_PART

使用BEGIN_CONNECTION_PART宏開始定義事件和屬性通知連接點以外的其他連接點。

```
BEGIN_CONNECTION_PART(theClass, localClass)
```

### <a name="parameters"></a>參數

*類別*<br/>
指定連接點為該連接點的控制項類的名稱。

*localClass*<br/>
指定實作連接點之區域類別的名稱。

### <a name="remarks"></a>備註

在定義類成員函數的聲明 (.h) 檔中,使用BEGIN_CONNECTION_PART宏啟動連接點,然後添加CONNECTION_IID宏和要實現的任何其他成員函數,然後使用END_CONNECTION_PART宏完成連接點映射。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="end_connection_part"></a><a name="end_connection_part"></a>END_CONNECTION_PART

結束連接點的宣告。

```
END_CONNECTION_PART(localClass)
```

### <a name="parameters"></a>參數

*localClass*<br/>
指定實作連接點之區域類別的名稱。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="connection_iid"></a><a name="connection_iid"></a>CONNECTION_IID

在BEGIN_CONNECTION_PART和END_CONNECTION_PART宏之間使用為 OLE 控制項支援的連接點定義介面 ID。

```
CONNECTION_IID(iid)
```

### <a name="parameters"></a>參數

*Iid*<br/>
連接點所呼叫介面的介面 ID。

### <a name="remarks"></a>備註

*iid*參數是一個介面 ID,用於標識連接點將在其連接的接收器上調用的介面。 例如：

[!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]

指定呼叫 `ISinkInterface` 介面的連接點。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="declare_connection_map"></a><a name="declare_connection_map"></a>DECLARE_CONNECTION_MAP

程式中的每個 `COleControl` 衍生類別都可以提供一個連接對應，用於指定您的控制項所支援的其他連接點。

```
DECLARE_CONNECTION_MAP()
```

### <a name="remarks"></a>備註

如果控件支援其他點,請使用類聲明末尾的DECLARE_CONNECTION_MAP宏。 然後,在定義類成員函數的 .cpp 檔中,使用BEGIN_CONNECTION_MAP宏,CONNECTION_PART每個控件的連接點CONNECTION_PART宏,END_CONNECTION_MAP宏來聲明連接映射的結束。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="begin_connection_map"></a><a name="begin_connection_map"></a>BEGIN_CONNECTION_MAP

程式中每個 `COleControl` 衍生類別可以提供連接對應，以指定控制項支援的連接點。

```
BEGIN_CONNECTION_MAP(theClass, theBase)
```

### <a name="parameters"></a>參數

*類別*<br/>
指定連接對應之控制項類別的名稱。

*theBase*<br/>
指定*類*的基類的名稱。

### <a name="remarks"></a>備註

在實現中 (.CPP) 檔案,用於定義類的成員函數,使用BEGIN_CONNECTION_MAP宏啟動連接映射,然後使用[CONNECTION_PART](#connection_part)宏為每個連接點添加宏條目。 最後,使用[END_CONNECTION_MAP](#end_connection_map)宏完成連接映射。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="end_connection_map"></a><a name="end_connection_map"></a>END_CONNECTION_MAP

結束連接對應的定義。

```
END_CONNECTION_MAP()
```

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="connection_part"></a><a name="connection_part"></a>CONNECTION_PART

將 OLE 控制元件的連接點映射到特定的介面 ID。

```
CONNECTION_PART(theClass, iid, localClass)
```

### <a name="parameters"></a>參數

*類別*<br/>
指定連接點為該連接點的控制項類的名稱。

*Iid*<br/>
連接點所呼叫介面的介面 ID。

*localClass*<br/>
指定實作連接點之區域類別的名稱。

### <a name="remarks"></a>備註

例如：

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]

實現連接映射,連接點,呼叫`IID_ISinkInterface`介面 。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="afxconnectionadvise"></a><a name="afxconnectionadvise"></a>AfxConnection 建議

呼叫此函數以建立由*pUnkSrc*指定的源和*pUnkSink*指定的接收器之間的連接。

```
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD FAR* pdwCookie);
```

### <a name="parameters"></a>參數

*普恩克斯克*<br/>
指向調用介面的物件的指標。

*pUnkSink*<br/>
指向實現介面的物件的指標。

*Iid*<br/>
連接的介面 ID。

*bRef( B) Count*<br/>
TRUE 表示創建連接應導致*pUnkSink*的引用計數增加。 FALSE 表示不應增加引用計數。

*pdwCookie*<br/>
指向返回連接標識碼的 DWORD 的指標。 斷開連接時,此值應作為*dwCookie*`AfxConnectionUnadvise`參數傳遞給。

### <a name="return-value"></a>傳回值

建立連接時非零;否則 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]

### <a name="requirements"></a>需求

**標題:** afxctl.h

## <a name="afxconnectionunadvise"></a><a name="afxconnectionunadvise"></a>AfxConnectionUn建議

呼叫此函數以斷開由*pUnkSrc*指定的源和*pUnkSink*指定的接收器之間的連接。

```
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD dwCookie);
```

### <a name="parameters"></a>參數

*普恩克斯克*<br/>
指向調用介面的物件的指標。

*pUnkSink*<br/>
指向實現介面的物件的指標。

*Iid*<br/>
連接點介面的介面 ID。

*bRef( B) Count*<br/>
TRUE 表示斷開連接應會導致*pUnkSink*的引用計數被遞減。 FALSE 表示不應減少引用計數。

*dwCookie*<br/>
傳`AfxConnectionAdvise`回的連接識別碼。

### <a name="return-value"></a>傳回值

如果連接斷開,則非零;否則 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]

### <a name="requirements"></a>需求

**標題:** afxctl.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
