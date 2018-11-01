---
title: CComClassFactory 類別
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
ms.openlocfilehash: 61dd67a4a34be447807799537971c19c11d09e5e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575223"
---
# <a name="ccomclassfactory-class"></a>CComClassFactory 類別

這個類別會實作[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)介面。

## <a name="syntax"></a>語法

```
class CComClassFactory
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComClassFactory::CreateInstance](#createinstance)|建立指定的 CLSID 的物件。|
|[CComClassFactory::LockServer](#lockserver)|鎖定記憶體中的 class factory。|

## <a name="remarks"></a>備註

`CComClassFactory` 會實作[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)介面，其中包含用於建立特定的 CLSID 的物件，以及鎖定的 class factory，以允許更快速地建立新物件的記憶體中的方法。 `IClassFactory` 必須針對您要註冊在系統登錄，並將您指派為 CLSID 的每個類別實作。

ATL 物件通常取得 class factory 藉由衍生自[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 這個類別包含巨集[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)，其中宣告`CComClassFactory`做為預設 class factory。 若要覆寫此預設值，指定的其中一個`DECLARE_CLASSFACTORY` *XXX*類別定義中的巨集。 例如， [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex)巨集的 class factory 會使用指定的類別：

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

上述的類別定義指定`CMyClassFactory`將用於做為物件的預設 class factory。 `CMyClassFactory` 必須衍生自`CComClassFactory`，並覆寫`CreateInstance`。

ATL 提供三個其他宣告 class factory 的巨集：

- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)會使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)，這會控制透過授權的建立。

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)會使用[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)，這會建立在多個 apartment 中的物件。

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton)會使用[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)，這會建構單一[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)物件。

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="createinstance"></a>  CComClassFactory::CreateInstance

建立指定的 CLSID 的物件，並擷取此物件的介面指標。

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

##  <a name="lockserver"></a>  CComClassFactory::LockServer

遞增和遞減模組鎖定計數藉由呼叫`_Module::Lock`和`_Module::Unlock`分別。

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>參數

*fLock*<br/>
[in]如果為 TRUE，就會遞增的鎖定計數;否則，鎖定計數會遞減。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

`_Module` 全域執行個體是指[CComModule](../../atl/reference/ccommodule-class.md)或從它衍生的類別。

呼叫`LockServer`允許用戶端，以便可以快速建立多個物件保留的 class factory。

## <a name="see-also"></a>另請參閱

[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[類別概觀](../../atl/atl-class-overview.md)
