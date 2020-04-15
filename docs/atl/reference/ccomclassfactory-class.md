---
title: CComClass 工廠類別
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
ms.openlocfilehash: 041575339906b83488697f1db5a7f8b08b53070e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321027"
---
# <a name="ccomclassfactory-class"></a>CComClass 工廠類別

此類實現[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)介面。

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
|[CComClass 工廠:建立實體](#createinstance)|建立指定的 CLSID 的物件。|
|[CComClass 工廠::鎖伺服器](#lockserver)|將類工廠鎖定在記憶體中。|

## <a name="remarks"></a>備註

`CComClassFactory`實現[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)介面,其中包含用於創建特定CLSID物件的方法,以及將類工廠鎖定在記憶體中,以便更快地創建新物件。 `IClassFactory`必須針對在系統註冊表中註冊併為其分配 CLSID 的每個類實現。

ATL 物件通常透過[CComCoClass](../../atl/reference/ccomcoclass-class.md)獲得類工廠。 此類包括宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)`CComClassFactory`,它 聲明為預設類工廠。 要重寫此預設值,請在類定義中`DECLARE_CLASSFACTORY`指定*XXX*宏之一。 例如[,DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex)宏對類工廠使用指定的類:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

上面的類定義指定`CMyClassFactory`將用作對象的預設類工廠。 `CMyClassFactory`必須指定並`CComClassFactory`覆`CreateInstance`寫 。

ATL 提供聲明類工廠的其他三個宏:

- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md),它控制通過許可證創建的。

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)使用[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md),它可在多個單元中創建物件。

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton)使用[CComClassFactory 單一項](../../atl/reference/ccomclassfactorysingleton-class.md),它建構單個[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)物件。

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ccomclassfactorycreateinstance"></a><a name="createinstance"></a>CComClass 工廠:建立實體

建立指定的 CLSID 的物件並檢索指向此物件的介面指標。

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>參數

*pUnkOuter*<br/>
[在]如果對像是作為聚合的一部分創建的,則*pUnkOuter*必須是外部未知物件。 否則 *,pUnkOuter*必須為 NULL。

*riid*<br/>
[在]請求介面的 IID。 如果*pUnkOuter*是非 NULL, 則`IID_IUnknown`*riid*必須為 。

*普夫奧比*<br/>
[出]指向*riid*標識的介面指標的指標。 如果物件不支援此介面,*則 ppvObj*設定為 NULL。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="ccomclassfactorylockserver"></a><a name="lockserver"></a>CComClass 工廠::鎖伺服器

遞增與遞減模組鎖定計數分別透過呼`_Module::Lock`叫`_Module::Unlock`與 。

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>參數

*羊群*<br/>
[在]如果為 TRUE,則鎖計數將遞增;如果為 TRUE,則鎖定計數將遞增。否則,鎖計數將遞減。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

`_Module`指[CComModule](../../atl/reference/ccommodule-class.md)的全域實例或從它派生的類。

調用`LockServer`允許用戶端保留類工廠,以便可以快速創建多個物件。

## <a name="see-also"></a>另請參閱

[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThread模型](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[類別概觀](../../atl/atl-class-overview.md)
