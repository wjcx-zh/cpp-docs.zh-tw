---
title: CComClass 工廠單頓類別
ms.date: 11/04/2016
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
ms.openlocfilehash: ec860f7ef59b7d3289bf2e18fea0f0e064a7c8f9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320811"
---
# <a name="ccomclassfactorysingleton-class"></a>CComClass 工廠單頓類別

此類派生自[CComClassFactory,](../../atl/reference/ccomclassfactory-class.md)並使用[CComObject Global](../../atl/reference/ccomobjectglobal-class.md)構造單個物件。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

#### <a name="parameters"></a>參數

*T*<br/>
你的班級

`CComClassFactorySingleton`派生自[CComClassFactory,](../../atl/reference/ccomclassfactory-class.md)並使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)構造單個物件。 對方法`CreateInstance`的每個調用都只是查詢此對象作為介面指標。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComClass 工廠單一::建立實體](#createinstance)|介面指標`m_spObj`的查詢。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComClass工廠單頓::m_spObj](#m_spobj)|由 建構`CComClassFactorySingleton`的[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)物件。|

## <a name="remarks"></a>備註

ATL 物件通常透過[CComCoClass](../../atl/reference/ccomcoclass-class.md)獲得類工廠。 此類包括宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)`CComClassFactory`,它 聲明為預設類工廠。 要使用`CComClassFactorySingleton`,請在物件的類定義中指定[DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton)宏。 例如：

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

[CComClass 工廠](../../atl/reference/ccomclassfactory-class.md)

`CComClassFactorySingleton`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ccomclassfactorysingletoncreateinstance"></a><a name="createinstance"></a>CComClass 工廠單一::建立實體

通過`QueryInterface`[m_spObj](#m_spobj)調用以檢索介面指標。

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

## <a name="ccomclassfactorysingletonm_spobj"></a><a name="m_spobj"></a>CComClass工廠單頓::m_spObj

由 建構`CComClassFactorySingleton`的[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)物件。

```
CComPtr<IUnknown> m_spObj;
```

### <a name="remarks"></a>備註

[對 CreateInstance](#createinstance)方法的每個調用都只是查詢此物件以作為介面指標。

請注意,當前`m_spObj`形式的與以前版本的 ATL`CComClassFactorySingleton`的工作方式相比,存在重大變化。 在以前的版本中,`CComClassFactorySingleton`對像是在伺服器初始化期間與類工廠同時創建的。 在 Visual C++.NET 2003 及更高版本中,物件在第一個請求上被懶惰地創建。 此更改可能會導致依賴於早期初始化的程式中的錯誤。

## <a name="see-also"></a>另請參閱

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2 類別](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComclass 工廠自動線程類別](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThread模型](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[類別概觀](../../atl/atl-class-overview.md)
