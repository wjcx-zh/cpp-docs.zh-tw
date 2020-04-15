---
title: IEnumonSTLimpl 類別
ms.date: 11/04/2016
f1_keywords:
- IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl::Clone
- ATLCOM/ATL::IEnumOnSTLImpl::Init
- ATLCOM/ATL::IEnumOnSTLImpl::Next
- ATLCOM/ATL::IEnumOnSTLImpl::Reset
- ATLCOM/ATL::IEnumOnSTLImpl::Skip
- ATLCOM/ATL::IEnumOnSTLImpl::m_iter
- ATLCOM/ATL::IEnumOnSTLImpl::m_pcollection
- ATLCOM/ATL::IEnumOnSTLImpl::m_spUnk
helpviewer_keywords:
- IEnumOnSTLImpl class
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
ms.openlocfilehash: 2fbe6ccfbea2836c42a054da7ea9ebeac4e1555d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329704"
---
# <a name="ienumonstlimpl-class"></a>IEnumonSTLimpl 類別

此類基於C++標準庫集合定義枚舉器介面。

## <a name="syntax"></a>語法

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```

#### <a name="parameters"></a>參數

*基地*<br/>
COM 枚舉器。 有關示例,請參閱[IEnumString。](/windows/win32/api/objidl/nn-objidl-ienumstring)

*皮伊德*<br/>
指向枚舉器介面介面的介面 ID 的指標。

*T*<br/>
枚舉器介面公開的項的類型。

*複製*<br/>
[複製原則類別](../../atl/atl-copy-policy-classes.md)。

*拼貼*<br/>
C++標準庫容器類。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IEnumonSTLimpl::複製](#clone)|**克隆**的實現。|
|[IEnumonSTLimpl::Init](#init)|初始化列舉程式。|
|[IEnumonSTLimpl::下一個](#next)|下**一步**的實施。|
|[IEnumonSTLimpl::重置](#reset)|**複位**的實現。|
|[IEnumonSTLimpl::跳過](#skip)|**Skip**的實現。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[IEnumonSTLimpl::m_iter](#m_iter)|表示枚舉器在集合中的當前位置的反覆運算器。|
|[IEnumonSTLimpl::m_pcollection](#m_pcollection)|指向C++標準庫容器的指標,該容器包含要枚舉的專案。|
|[IEnumonSTLimpl::m_spUnk](#m_spunk)|提供`IUnknown`集合的物件的指標。|

## <a name="remarks"></a>備註

`IEnumOnSTLImpl`提供 COM 枚舉器介面的實現,其中枚舉的專案存儲在與標準庫相容的 C++容器中。 此類類似於[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)類,該類為基於陣列的枚舉器介面提供了實現。

> [!NOTE]
> 請參閱[CComEnumImpl::init](../../atl/reference/ccomenumimpl-class.md#init)`CComEnumImpl``IEnumOnSTLImpl`有關 和 之間的進一步差異的詳細資訊。

通常,不需要通過*not*派生此介面實現創建自己的枚舉器類。 如果要使用基於C++標準庫容器的 ATL 提供的枚舉器,則更常見的是創建[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)實例,或者創建一個集合類,該集合類通過派生自[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)來返回枚舉器。

但是,如果確實需要提供自定義枚舉器(例如,除了枚舉器介面外公開介面),則可以從此類派生。 在此情況下,您可能需要重寫[Clone](#clone)方法以提供您自己的實現。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Base`

`IEnumOnSTLImpl`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ienumonstlimplinit"></a><a name="init"></a>IEnumonSTLimpl::Init

初始化列舉程式。

```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```

### <a name="parameters"></a>參數

*pUnkfor 釋放*<br/>
[在]在`IUnknown`枚舉器的生存期內必須保持活動的物件的指標。 如果不存在此類物件,則傳遞 NULL。

*收集*<br/>
對保存要枚舉的專案C++標準庫容器的引用。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

如果傳遞`Init`對另一個物件中保存的集合的引用,則可以使用*pUnkForRelease*參數來確保只要枚舉器需要,該物件及其保留的集合就可用。

在將指向枚舉器介面的指標傳回任何用戶端之前,必須調用此方法。

## <a name="ienumonstlimplclone"></a><a name="clone"></a>IEnumonSTLimpl::複製

此方法通過創建類型`CComEnumOnSTL`物件、使用當前物件使用的相同集合和反覆運算器初始化它,並在新創建的物件上返回介面來提供**Clone**方法的實現。

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>參數

*ppEnum*<br/>
[出]從當前枚舉器克隆的新創建物件的枚舉器介面。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="ienumonstlimplm_spunk"></a><a name="m_spunk"></a>IEnumonSTLimpl::m_spUnk

提供`IUnknown`集合的物件的指標。

```
CComPtr<IUnknown> m_spUnk;
```

### <a name="remarks"></a>備註

此智慧指標維護傳遞給[IEnumOnSTLImpl::init](#init)的物件的引用,確保它在枚舉器的生存期內保持活動狀態。

## <a name="ienumonstlimplm_pcollection"></a><a name="m_pcollection"></a>IEnumonSTLimpl::m_pcollection

此成員指向提供推動實現枚舉器介面的數據的集合。

```
CollType* m_pcollection;
```

### <a name="remarks"></a>備註

此成員通過調用[IEnumOnSTLImpl::Init](#init)初始化。

## <a name="ienumonstlimplm_iter"></a><a name="m_iter"></a>IEnumonSTLimpl::m_iter

此成員持有用於標記集合中的當前位置並導航到後續元素的反覆運算器。

```
CollType::iterator m_iter;
```

## <a name="ienumonstlimplnext"></a><a name="next"></a>IEnumonSTLimpl::下一個

此方法提供**Next**方法的實現。

```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```

### <a name="parameters"></a>參數

*celt*<br/>
[在]請求的元素數。

*格爾特*<br/>
[出]要用元素填充的陣列。

*pceltFetched*<br/>
[出]在*rgelt*中實際返回的元素數。 如果清單中保留少於*celt*元素,則這可能小於*celt。*

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="ienumonstlimplreset"></a><a name="reset"></a>IEnumonSTLimpl::重置

此方法提供**重置**方法的實現。

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="ienumonstlimplskip"></a><a name="skip"></a>IEnumonSTLimpl::跳過

此方法提供**Skip**方法的實現。

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>參數

*celt*<br/>
[在]要跳過的元素數。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
