---
title: CComClassFactoryAutoThread 類別
ms.date: 11/04/2016
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
ms.openlocfilehash: 73879a73a48290e19d2a27307884953129826df7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497483"
---
# <a name="ccomclassfactoryautothread-class"></a>CComClassFactoryAutoThread 類別

這個類別會實[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)介面，並允許在多個單元中建立物件。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CComClassFactoryAutoThread
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CComClassFactoryAutoThread::CreateInstance](#createinstance)|建立指定之 CLSID 的物件。|
|[CComClassFactoryAutoThread::LockServer](#lockserver)|鎖定記憶體中的 Class Factory。|

## <a name="remarks"></a>備註

`CComClassFactoryAutoThread`類似于[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，但允許在多個單元中建立物件。 若要利用這項支援，請從[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)衍生您的 EXE 模組。

ATL 物件通常會藉由衍生自[CComCoClass](../../atl/reference/ccomcoclass-class.md)來取得 Class Factory。 這個類別包含宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)，其會將[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)宣告為預設 Class Factory。 若要`CComClassFactoryAutoThread`使用，請在物件的類別定義中指定[DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)宏。 例如：

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]

## <a name="inheritance-hierarchy"></a>繼承階層

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

`CComClassFactoryAutoThread`

## <a name="requirements"></a>需求

**標頭：** atlcom.h。h

##  <a name="createinstance"></a>CComClassFactoryAutoThread：： CreateInstance

建立指定之 CLSID 的物件，並抓取這個物件的介面指標。

```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>參數

*pUnkOuter*<br/>
在如果將物件建立為匯總的一部分，則*pUnkOuter*必須是外部未知的。 否則， *pUnkOuter*必須是 Null。

*riid*<br/>
在所要求介面的 IID。 如果*pUnkOuter*為非 Null，則*riid*必須是`IID_IUnknown`。

*ppvObj*<br/>
脫銷由*riid*識別之介面指標的指標。 如果物件不支援這個介面， *ppvObj*會設定為 Null。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

如果您的模組衍生自 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) `CreateInstance`，請先選取要在相關聯的單元中建立物件的執行緒。

##  <a name="lockserver"></a>CComClassFactoryAutoThread：： LockServer

分別呼叫`_Module::Lock`和`_Module::Unlock`，以遞增和遞減模組鎖定計數。

```
STDMETHODIMP LockServer(BOOL fLock);
```

### <a name="parameters"></a>參數

*fLock*<br/>
在若為 TRUE，則鎖定計數會遞增;否則，鎖定計數就會遞減。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

使用`CComClassFactoryAutoThread`時， `_Module`通常是指[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)的全域實例。

呼叫`LockServer`可讓用戶端保存到 Class Factory，以便快速建立多個物件。

## <a name="see-also"></a>另請參閱

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2 類別](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactorySingleton 類別](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[類別總覽](../../atl/atl-class-overview.md)
