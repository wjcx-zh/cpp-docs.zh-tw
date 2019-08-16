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
ms.openlocfilehash: 892153e47ac4e9dd45d5dfc01b76f1ce29d23938
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497443"
---
# <a name="ccomclassfactory-class"></a>CComClassFactory 類別

這個類別會實[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)介面。

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
|[CComClassFactory::CreateInstance](#createinstance)|建立指定之 CLSID 的物件。|
|[CComClassFactory::LockServer](#lockserver)|鎖定記憶體中的 Class Factory。|

## <a name="remarks"></a>備註

`CComClassFactory`會執行[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)介面, 其中包含用來建立特定 CLSID 物件的方法, 以及鎖定記憶體中的 Class Factory, 讓新物件可以更快速地建立。 `IClassFactory`必須針對您在系統登錄中註冊的每個類別, 以及您要指派 CLSID 的來執行。

ATL 物件通常會藉由衍生自[CComCoClass](../../atl/reference/ccomcoclass-class.md)來取得 Class Factory。 這個類別包含宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), 它`CComClassFactory`會宣告為預設 Class Factory。 若要覆寫此預設值, 請`DECLARE_CLASSFACTORY`在您的類別定義中指定其中一個*XXX*宏。 例如, [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex)宏會針對 Class Factory 使用指定的類別:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

上述類別定義`CMyClassFactory`會指定將用來做為物件的預設 Class Factory。 `CMyClassFactory`必須衍生自`CComClassFactory` , 而且`CreateInstance`會覆寫。

ATL 提供其他三個宣告 Class Factory 的宏:

- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)會使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), 透過授權來控制建立。

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)會使用[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), 以在多個單元中建立物件。

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton)會使用[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), 它會構造單一[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)物件。

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

##  <a name="createinstance"></a>CComClassFactory:: CreateInstance

建立指定之 CLSID 的物件, 並抓取這個物件的介面指標。

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

##  <a name="lockserver"></a>  CComClassFactory::LockServer

分別呼叫`_Module::Lock`和`_Module::Unlock`, 以遞增和遞減模組鎖定計數。

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>參數

*fLock*<br/>
在若為 TRUE, 則鎖定計數會遞增;否則, 鎖定計數就會遞減。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

`_Module`指的是[CComModule](../../atl/reference/ccommodule-class.md)的全域實例或衍生自它的類別。

呼叫`LockServer`可讓用戶端保存到 Class Factory, 以便快速建立多個物件。

## <a name="see-also"></a>另請參閱

[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[類別總覽](../../atl/atl-class-overview.md)
