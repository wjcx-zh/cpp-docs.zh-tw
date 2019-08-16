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
ms.openlocfilehash: 71705d02140f0392a9ce023c64e7b4125c14443f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497396"
---
# <a name="ccomclassfactorysingleton-class"></a>CComClassFactorySingleton 類別

這個類別衍生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md) , 並使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)來建立單一物件。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別。

`CComClassFactorySingleton`衍生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md) , 並使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)來建立單一物件。 每次呼叫`CreateInstance`方法時, 只會查詢此物件的介面指標。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CComClassFactorySingleton::CreateInstance](#createinstance)|介面`m_spObj`指標的查詢。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CComClassFactorySingleton::m_spObj](#m_spobj)|所建立的[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)物件`CComClassFactorySingleton`。|

## <a name="remarks"></a>備註

ATL 物件通常會藉由衍生自[CComCoClass](../../atl/reference/ccomcoclass-class.md)來取得 Class Factory。 這個類別包含宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), 它`CComClassFactory`會宣告為預設 Class Factory。 若要`CComClassFactorySingleton`使用, 請在物件的類別定義中指定[DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton)宏。 例如：

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]

## <a name="inheritance-hierarchy"></a>繼承階層

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)

`CComClassFactorySingleton`

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

##  <a name="createinstance"></a>CComClassFactorySingleton:: CreateInstance

透過`QueryInterface` [m_spObj](#m_spobj)呼叫以取得介面指標。

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>參數

*pUnkOuter*<br/>
在如果將物件建立為匯總的一部分, 則*pUnkOuter*必須是外部未知的。 否則, *pUnkOuter*必須是 Null。

*riid*<br/>
在所要求介面的 IID。 如果*pUnkOuter*為非 Null, 則*riid*必須是`IID_IUnknown`。

*ppvObj*<br/>
脫銷由*riid*識別之介面指標的指標。 如果物件不支援這個介面, *ppvObj*會設定為 Null。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="m_spobj"></a>CComClassFactorySingleton::m_spObj

所建立的[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)物件`CComClassFactorySingleton`。

```
CComPtr<IUnknown> m_spObj;
```

### <a name="remarks"></a>備註

每次呼叫[CreateInstance](#createinstance)方法時, 只會針對介面指標查詢這個物件。

請注意, 目前的形式`m_spObj`呈現了在舊版 ATL 中運作`CComClassFactorySingleton`方式的中斷性變更。 在先前版本`CComClassFactorySingleton`中, 物件是在伺服器初始化期間與 Class Factory 同時建立的。 在 Visual C++.net 2003 和更新版本中, 會在第一個要求時延遲建立物件。 這項變更可能會導致依賴早期初始化的程式發生錯誤。

## <a name="see-also"></a>另請參閱

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2 類別](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactoryAutoThread 類別](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[類別總覽](../../atl/atl-class-overview.md)
