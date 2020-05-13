---
title: CComclass 工廠自動線程類別
ms.date: 11/04/2016
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
ms.openlocfilehash: e997d92adfa9df46c82dacbd297db495b037c6e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320910"
---
# <a name="ccomclassfactoryautothread-class"></a>CComclass 工廠自動線程類別

此類實現[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)介面,並允許在多個單元中創建物件。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CComClassFactoryAutoThread
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComClass 工廠自動線程:建立實體](#createinstance)|建立指定的 CLSID 的物件。|
|[CComclass 工廠自動線程:鎖定伺服器](#lockserver)|將類工廠鎖定在記憶體中。|

## <a name="remarks"></a>備註

`CComClassFactoryAutoThread`類似於[CComClassFactory,](../../atl/reference/ccomclassfactory-class.md)但允許在多個公寓中創建物件。 要利用此支援,請從[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)派生 EXE 模組。

ATL 物件通常透過[CComCoClass](../../atl/reference/ccomcoclass-class.md)獲得類工廠。 此類包括宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory),它聲明[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)為預設類工廠。 要使用`CComClassFactoryAutoThread`,請在物件的類定義中指定[DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)宏。 例如：

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

`CComClassFactoryAutoThread`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ccomclassfactoryautothreadcreateinstance"></a><a name="createinstance"></a>CComClass 工廠自動線程:建立實體

建立指定的 CLSID 的物件並檢索指向此物件的介面指標。

```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
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

### <a name="remarks"></a>備註

如果模組派生自[CComAutoThreadModule,](../../atl/reference/ccomautothreadmodule-class.md)`CreateInstance`則首先選擇一個線程在關聯的單元中創建物件。

## <a name="ccomclassfactoryautothreadlockserver"></a><a name="lockserver"></a>CComclass 工廠自動線程:鎖定伺服器

遞增與遞減模組鎖定計數分別透過呼`_Module::Lock`叫`_Module::Unlock`與 。

```
STDMETHODIMP LockServer(BOOL fLock);
```

### <a name="parameters"></a>參數

*羊群*<br/>
[在]如果為 TRUE,則鎖計數將遞增;如果為 TRUE,則鎖定計數將遞增。否則,鎖計數將遞減。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

使用`CComClassFactoryAutoThread``_Module`時 ,通常引用[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)的全域實例。

調用`LockServer`允許用戶端保留類工廠,以便可以快速創建多個物件。

## <a name="see-also"></a>另請參閱

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2 類別](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClass 工廠單頓類別](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThread模型](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[類別概觀](../../atl/atl-class-overview.md)
