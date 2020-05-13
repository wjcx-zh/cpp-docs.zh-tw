---
title: CCachedDataPathProperty 類別
ms.date: 11/04/2016
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
helpviewer_keywords:
- CCachedDataPathProperty [MFC], CCachedDataPathProperty
- CCachedDataPathProperty [MFC], m_Cache
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
ms.openlocfilehash: ebab34433f23b119e3444b3eaa8b0ad6313555af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352371"
---
# <a name="ccacheddatapathproperty-class"></a>CCachedDataPathProperty 類別

實作非同步傳輸且在記憶體檔案中快取的 OLE 控制項屬性。

## <a name="syntax"></a>語法

```
class CCachedDataPathProperty : public CDataPathProperty
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCached 資料路徑屬性:CCachedDataPath屬性](#ccacheddatapathproperty)|建構 `CCachedDataPathProperty` 物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CCachedDataPath 屬性::m_Cache](#m_cache)|`CMemFile`要在其中緩存數據的物件。|

## <a name="remarks"></a>備註

記憶體檔案儲存在 RAM 中而不是磁碟上,可用於快速臨時傳輸。

與`CAysncMonikerFile``CDataPathProperty``CCachedDataPathProperty`和 一起提供了在 OLE 控制項中使用非同步名字器的功能。 對於`CCachedDataPathProperty`物件,您可以從 URL 或檔源非同步傳輸資料`m_Cache`,並透過公共變數將其儲存在記憶體檔中。 所有資料都存儲在記憶體檔中,除非您想要監視通知並回應,否則無需覆蓋[OnDataFor。](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable) 例如,如果要傳輸較大的 。GIF 檔,並希望通知您的控件,更多的數據已經到來,它應該重新繪製本身,重`OnDataAvailable`寫 以發出通知。

類別`CCachedDataPathProperty`的類別`CDataPathProperty`。

有關如何在 Internet 應用程式中使用非同步名字器和 ActiveX 控制件的詳細資訊,請參閱以下主題:

- [互聯網第一步:主動X控制](../../mfc/activex-controls-on-the-internet.md)

- [互聯網第一步:異步月友](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStream 檔案](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)

`CCachedDataPathProperty`

## <a name="requirements"></a>需求

**標題:** afxctl.h

## <a name="ccacheddatapathpropertyccacheddatapathproperty"></a><a name="ccacheddatapathproperty"></a>CCached 資料路徑屬性:CCachedDataPath屬性

建構 `CCachedDataPathProperty` 物件。

```
CCachedDataPathProperty(COleControl* pControl = NULL);

CCachedDataPathProperty(
    LPCTSTR lpszPath,
    COleControl* pControl = NULL);
```

### <a name="parameters"></a>參數

*pControl*<br/>
指向要與此`CCachedDataPathProperty`物件關聯的 ActiveX 控制件物件的指標。

*lpszPath*<br/>
路徑可以是絕對的或相對的,用於創建引用屬性的實際絕對位置的異步名字物件。 `CCachedDataPathProperty`使用 URL,而不是檔案名。 如果需要文件`CCachedDataPathProperty`的物件,則file://路徑進行預準備。

### <a name="remarks"></a>備註

`COleControl` *pControl*指向的物件由[Open](../../mfc/reference/cdatapathproperty-class.md#open)使用,並由派生類檢索。 如果*pControl*為 NULL,則應`Open`使用[SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol)設定 與 中使用的控制項。 如果*lpszPath*為 NULL,則`Open`可以在路徑中 透過路徑或使用[SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath)設定它。

## <a name="ccacheddatapathpropertym_cache"></a><a name="m_cache"></a>CCachedDataPath 屬性::m_Cache

包含緩存數據的記憶體檔的類名。

```
CMemFile m_Cache;
```

### <a name="remarks"></a>備註

記憶體檔案儲存在 RAM 中,而不是儲存在磁碟上。

## <a name="see-also"></a>另請參閱

[CDataPathProperty 類別](../../mfc/reference/cdatapathproperty-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDataPathProperty 類別](../../mfc/reference/cdatapathproperty-class.md)
