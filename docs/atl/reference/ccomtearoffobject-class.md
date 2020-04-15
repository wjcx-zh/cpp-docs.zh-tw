---
title: CComTearoff 物件類別
ms.date: 11/04/2016
f1_keywords:
- CComTearOffObject
- ATLCOM/ATL::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::AddRef
- ATLCOM/ATL::CComTearOffObject::QueryInterface
- ATLCOM/ATL::CComTearOffObject::Release
- ATLCOM/ATL::CComTearOffObjectBase
- ATLCOM/ATL::m_pOwner
helpviewer_keywords:
- tear-off interfaces, ATL
- tear-off interfaces
- CComTearOffObject class
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
ms.openlocfilehash: de7528d3972991c233ee4b9037f609b89d0f7434
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327314"
---
# <a name="ccomtearoffobject-class"></a>CComTearoff 物件類別

此類實現分機介面。

## <a name="syntax"></a>語法

```
template<class Base>
class CComTearOffObject : public Base
```

#### <a name="parameters"></a>參數

*基地*<br/>
您的拆解類,派生自`CComTearOffObjectBase`您希望拆解物件支援的介面。

ATL分兩個階段實現其分管介面`CComTearOffObjectBase`- 該方法處理引用計`QueryInterface`數和`CComTearOffObject`,同時 實現[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComTEARoff 物件:CComtearoff 物件](#ccomtearoffobject)|建構函式。|
|[CComTEARoff 物件:*CComtearoff 物件](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComTearoff 物件::新增參考](#addref)|增加`CComTearOffObject`物件的引用計數。|
|[CComtearoff 物件::查詢介面](#queryinterface)|返回指向拆解類或擁有者類上請求介面的指標。|
|[CComTearOff 物件::發佈](#release)|取消`CComTearOffObject`物件的引用計數並銷毀它。|

### <a name="ccomtearoffobjectbase-methods"></a>CComTEAROff 物件基礎方法

|||
|-|-|
|[CComTEAROff 物件庫](#ccomtearoffobjectbase)|建構函式。|

### <a name="ccomtearoffobjectbase-data-members"></a>CComTEAROff 物件基礎資料成員

|||
|-|-|
|[m_pOwner](#m_powner)|指向從擁有者類`CComObject`派生的指標。|

## <a name="remarks"></a>備註

`CComTearOffObject`實現拆解介面作為單獨的物件,僅在查詢該介面時實例化。 當其引用計數變為零時,將刪除拆解。 通常,為很少使用的介面構建分機介面,因為使用分淚將 vtable 指標保存在主物件的所有實例中。

應派生實現撕掉的類,`CComTearOffObjectBase`並從希望拆解物件支援哪個介面派生。 `CComTearOffObjectBase`在擁有者類和線程模型上範本化。 擁有者類是正在為其實現撕掉的物件的類。 如果不指定線程模型,則使用預設線程模型。

應為拆解類創建 COM 映射。 當 ATL 實體化撕裂時,它會`CComTearOffObject<CYourTearOffClass>`建立`CComCachedTearOffObject<CYourTearOffClass>`或 。

例如,在 BEEPER 範例`CBeeper2`中, 類別是撕`CBeeper`掉類, 類別是擁有者類:

[!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Base`

`CComTearOffObject`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ccomtearoffobjectaddref"></a><a name="addref"></a>CComTearoff 物件::新增參考

將`CComTearOffObject`物件的引用計數增加一個。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

可用於診斷和測試的值。

## <a name="ccomtearoffobjectccomtearoffobject"></a><a name="ccomtearoffobject"></a>CComTEARoff 物件:CComtearoff 物件

建構函式。

```
CComTearOffObject(void* pv);
```

### <a name="parameters"></a>參數

*光伏*<br/>
[在]將轉換為指向物件的指標的`CComObject<Owner>`指標。

### <a name="remarks"></a>備註

將擁有者的引用計數增加一個。

## <a name="ccomtearoffobjectccomtearoffobject"></a><a name="dtor"></a>CComTEARoff 物件:*CComtearoff 物件

解構函式。

```
~CComTearOffObject();
```

### <a name="remarks"></a>備註

釋放所有分配的資源,調用 FinalRelease,並遞減模組鎖計數。

## <a name="ccomtearoffobjectccomtearoffobjectbase"></a><a name="ccomtearoffobjectbase"></a>CComTEARoff 物件:CComtearoff 物件庫

建構函式。

```
CComTearOffObjectBase();
```

### <a name="remarks"></a>備註

將[m_pOwner](#m_powner)成員初始化為 NULL。

## <a name="ccomtearoffobjectm_powner"></a><a name="m_powner"></a>CComTearoff 物件::m_pOwner

指向從*擁有者*派生的[CComObject](../../atl/reference/ccomobject-class.md)物件的指標。

```
CComObject<Owner>* m_pOwner;
```

### <a name="parameters"></a>參數

*擁有者*<br/>
[在]正在為其實現撕扯的類。

### <a name="remarks"></a>備註

指標在建構期間初始化為 NULL。

## <a name="ccomtearoffobjectqueryinterface"></a><a name="queryinterface"></a>CComtearoff 物件::查詢介面

擷取所要求介面的指標。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>參數

*Iid*<br/>
[在]請求的介面的 IID。

*ppvObject*<br/>
[出]指向*iid*識別的介面指標,如果找不到介面,則指向 NULL 的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

首先查詢拆解類上的介面。 如果介面不存在,則查詢所有者物件上的介面。 如果請求的介面為`IUnknown`,`IUnknown`則返回擁有者。

## <a name="ccomtearoffobjectrelease"></a><a name="release"></a>CComTearOff 物件::發佈

將引用計數除以 1,如果引用計數為零,則刪除`CComTearOffObject`。

```
STDMETHOD_ULONG Release();
```

### <a name="return-value"></a>傳回值

在非調試生成中,始終返回零。 在調試生成中,返回可用於診斷或測試的值。

## <a name="see-also"></a>另請參閱

[CComCachedTearOff物件類別](../../atl/reference/ccomcachedtearoffobject-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
