---
title: CComClassFactorySingleton 類別
ms.date: 11/04/2016
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
ms.openlocfilehash: 480b4c2a6e052e8e0823b97b548fc5d07b55230f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260171"
---
# <a name="ccomclassfactorysingleton-class"></a>CComClassFactorySingleton 類別

這個類別衍生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)並用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)來建構單一物件。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別。

`CComClassFactorySingleton` 衍生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)並用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)來建構單一物件。 每次呼叫`CreateInstance`方法只會查詢此物件的介面指標。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComClassFactorySingleton::CreateInstance](#createinstance)|查詢`m_spObj`介面指標。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComClassFactorySingleton::m_spObj](#m_spobj)|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)物件來建構`CComClassFactorySingleton`。|

## <a name="remarks"></a>備註

ATL 物件通常取得 class factory 藉由衍生自[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 這個類別包含巨集[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)，其中宣告`CComClassFactory`做為預設 class factory。 若要使用`CComClassFactorySingleton`，指定[DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton)物件的類別定義中的巨集。 例如：

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]

## <a name="inheritance-hierarchy"></a>繼承階層

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)

`CComClassFactorySingleton`

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="createinstance"></a>  CComClassFactorySingleton::CreateInstance

呼叫`QueryInterface`經由[m_spObj](#m_spobj)擷取介面指標。

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>參數

*pUnkOuter*<br/>
[in]如果物件過程中建立的彙總，然後*pUnkOuter*必須是外部未知。 否則，請*pUnkOuter*必須是 NULL。

*riid*<br/>
[in]要求的介面 IID。 如果*pUnkOuter*為非 NULL *riid*必須是`IID_IUnknown`。

*ppvObj*<br/>
[out]所識別之介面指標的指標*riid*。 如果物件不支援這個介面， *ppvObj*設為 NULL。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="m_spobj"></a>  CComClassFactorySingleton::m_spObj

[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)物件來建構`CComClassFactorySingleton`。

```
CComPtr<IUnknown> m_spObj;
```

### <a name="remarks"></a>備註

每次呼叫[CreateInstance](#createinstance)方法只會查詢此物件的介面指標。

請注意，目前的表單`m_spObj`提供一項重大變更的方式，`CComClassFactorySingleton`之前在舊版的 ATL 在舊版`CComClassFactorySingleton`與 class factory，同時在伺服器初始化期間建立物件。 在視覺效果C++.NET 2003 中，建立物件時，延遲的第一個要求。 這項變更可能導致錯誤，在早期初始化所依賴的程式。

## <a name="see-also"></a>另請參閱

[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2 類別](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactoryAutoThread 類別](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[類別概觀](../../atl/atl-class-overview.md)
