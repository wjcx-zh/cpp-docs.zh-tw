---
title: CComEnumimpl 類別
ms.date: 11/04/2016
f1_keywords:
- CComEnumImpl
- ATLCOM/ATL::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::Clone
- ATLCOM/ATL::CComEnumImpl::Init
- ATLCOM/ATL::CComEnumImpl::Next
- ATLCOM/ATL::CComEnumImpl::Reset
- ATLCOM/ATL::CComEnumImpl::Skip
- ATLCOM/ATL::CComEnumImpl::m_begin
- ATLCOM/ATL::CComEnumImpl::m_dwFlags
- ATLCOM/ATL::CComEnumImpl::m_end
- ATLCOM/ATL::CComEnumImpl::m_iter
- ATLCOM/ATL::CComEnumImpl::m_spUnk
helpviewer_keywords:
- CComEnumImpl class
ms.assetid: cc0d8e76-e608-46db-87cd-4c7161fe32d2
ms.openlocfilehash: 965e0a8bf6c890882754b60e2785832933d1c52c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327868"
---
# <a name="ccomenumimpl-class"></a>CComEnumimpl 類別

此類提供 COM 枚舉器介面的實現,其中枚舉的項存儲在陣列中。

## <a name="syntax"></a>語法

```
template <class Base,
    const IID* piid, class T, class Copy>
class ATL_NO_VTABLE CComEnumImpl : public Base
```

#### <a name="parameters"></a>參數

*基地*<br/>
COM 枚舉器介面。 有關示例,請參閱[IEnumString。](/windows/win32/api/objidl/nn-objidl-ienumstring)

*皮伊德*<br/>
指向枚舉器介面介面的介面 ID 的指標。

*T*<br/>
枚舉器介面公開的項的類型。

*複製*<br/>
同質[複製原則類別](../../atl/atl-copy-policy-classes.md)。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComenumimpl:ccomEnumimpl](#ccomenumimpl)|建構函式。|
|[CComenumimpl::_CComEnumimpl](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComEnumimpl:複製](#clone)|**克隆**枚舉介面方法的實現。|
|[CComenumimpl::Init](#init)|初始化列舉程式。|
|[CComEnumimpl::下一個](#next)|下**一步**的實施。|
|[CComEnumimpl::重置](#reset)|**複位**的實現。|
|[CComEnumimpl::跳過](#skip)|**Skip**的實現。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComEnumimpl::m_begin](#m_begin)|指向陣列中第一個項的指標。|
|[CComEnumimpl:m_dwFlags](#m_dwflags)|複製通過`Init`的標誌。|
|[CComEnumimpl:m_end](#m_end)|指向陣列中最後一個項之外的位置的指標。|
|[CComEnumimpl:m_iter](#m_iter)|指向陣列中當前項的指標。|
|[CComEnumimpl:m_spUnk](#m_spunk)|提供`IUnknown`要枚舉的集合的對象的指標。|

## <a name="remarks"></a>備註

有關方法實現的示例,請參閱[IEnumString。](/windows/win32/api/objidl/nn-objidl-ienumstring) `CComEnumImpl`提供 COM 枚舉器介面的實現,其中枚舉的項存儲在陣列中。 此類類似於類`IEnumOnSTLImpl`,該類提供基於C++標準庫容器的枚舉器介面的實現。

> [!NOTE]
> 有關`CComEnumImpl``IEnumOnSTLImpl`和之間的進一步差異的詳細資訊,請參閱[CComEnumImpl::init](#init)。

通常,不需要通過*not*派生此介面實現創建自己的枚舉器類。 如果要使用基於陣列的 ATL 提供的枚舉器,則創建[CComEnum](../../atl/reference/ccomenum-class.md)的實例更為常見。

但是,如果確實需要提供自定義枚舉器(例如,除了枚舉器介面外公開介面),則可以從此類派生。 在此情況下,您可能需要重寫[CComEnumImpl::Clone](#clone)方法來提供您自己的實現。

有關詳細資訊,請參閱[ATL 集合和枚舉器](../../atl/atl-collections-and-enumerators.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Base`

`CComEnumImpl`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ccomenumimplccomenumimpl"></a><a name="ccomenumimpl"></a>CComenumimpl:ccomEnumimpl

建構函式。

```
CComEnumImpl();
```

## <a name="ccomenumimplccomenumimpl"></a><a name="dtor"></a>CComenumimpl::_CComEnumimpl

解構函式。

```
~CComEnumImpl();
```

## <a name="ccomenumimplinit"></a><a name="init"></a>CComenumimpl::Init

在將指向枚舉器介面的指標傳回任何用戶端之前,必須調用此方法。

```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```

### <a name="parameters"></a>參數

*開始*<br/>
指向陣列的第一個元素的指標,其中包含要枚舉的項。

*結束*<br/>
指向陣列最後一個元素的位置的指標,其中包含要枚舉的項。

*龐克*<br/>
[在]在`IUnknown`枚舉器的生存期內必須保持活動的物件的指標。 如果不存在此類物件,則傳遞 NULL。

*標誌*<br/>
指示枚舉器是否應取得陣列的所有權或複製陣列的標誌。 下面將介紹可能的值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

只調用此方法一次 - 初始化枚舉器,使用它,然後扔掉它。

如果將指標傳遞給另一個物件中保留的陣列中的項(並且不要求枚舉器複製數據),則可以使用*pUnk*參數確保物件及其持有的陣列在枚舉器需要時可用。 枚舉器只需在物件上保存 COM 引用,即可使其保持活動狀態。 銷毀枚舉器時,將自動釋放 COM 引用。

*標誌*參數允許您指定枚舉器應如何處理傳遞給它的陣列元素。 *標誌*可以從下面所示`CComEnumFlags`的 枚舉中獲取其中一個值:

```
enum CComEnumFlags
   {
   AtlFlagNoCopy = 0,
   AtlFlagTakeOwnership = 2, // BitOwn
   AtlFlagCopy = 3           // BitOwn | BitCopy
   };
```

`AtlFlagNoCopy`表示陣列的生存期不受枚舉器控制。 在這種情況下,陣列將是靜態的,或者*pUnk*標識的物件將負責在不再需要陣列時釋放陣列。

`AtlFlagTakeOwnership`表示數組的銷毀由枚舉器控制。 在這種情況下,陣列必須使用**new**進行動態分配。 枚舉器將刪除其析構函數中的陣列。 通常,您將傳遞*pUnk*的 NULL,儘管如果您由於某種原因需要通知枚舉器的銷毀,您仍然可以傳遞有效的指標。

`AtlFlagCopy`表示要通過複製傳遞給`Init`的陣列來創建新陣列。 新陣列的存留期將由枚舉器控制。 枚舉器將刪除其析構函數中的陣列。 通常,您將傳遞*pUnk*的 NULL,儘管如果您由於某種原因需要通知枚舉器的銷毀,您仍然可以傳遞有效的指標。

> [!NOTE]
> 此方法的原型將數位元素指定為類型`T`,其中`T`定義為類的範本參數。 這是通過 COM 介面方法[CComEnumImpl:::next](#next)公開的相同類型。 這意味著,與[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)不同,此類不支援不同的存儲和公開數據類型。 陣列中元素的資料類型必須與透過 COM 介面公開的資料類型相同。

## <a name="ccomenumimplclone"></a><a name="clone"></a>CComEnumimpl:複製

此方法通過創建類型`CComEnum`物件、使用當前物件使用的相同陣列和反覆運算器初始化它,並在新創建的物件上返回介面來提供**Clone**方法的實現。

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>參數

*ppEnum*<br/>
[出]從當前枚舉器克隆的新創建物件的枚舉器介面。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

請注意,克隆的枚舉者永遠不會自行複製(或取得原始枚舉器使用的數據的擁有權)。 如有必要,克隆的枚舉器將保持原始枚舉器處於活動狀態(使用 COM 引用),以確保數據在需要時可用。

## <a name="ccomenumimplm_spunk"></a><a name="m_spunk"></a>CComEnumimpl:m_spUnk

此智慧指標維護傳遞給[CComEnumImpl::init](#init)的物件的引用,確保它在枚舉器的生存期內保持活動狀態。

```
CComPtr<IUnknown> m_spUnk;
```

## <a name="ccomenumimplm_begin"></a><a name="m_begin"></a>CComEnumimpl::m_begin

指向陣列最後一個元素的位置的指標,其中包含要枚舉的項。

```
T* m_begin;
```

## <a name="ccomenumimplm_end"></a><a name="m_end"></a>CComEnumimpl:m_end

指向陣列的第一個元素的指標,其中包含要枚舉的項。

```
T* m_end;
```

## <a name="ccomenumimplm_iter"></a><a name="m_iter"></a>CComEnumimpl:m_iter

指向陣列的當前元素的指標,其中包含要枚舉的項。

```
T* m_iter;
```

## <a name="ccomenumimplm_dwflags"></a><a name="m_dwflags"></a>CComEnumimpl:m_dwFlags

旗子傳遞給[CComEnumImpl:init。](#init)

```
DWORD m_dwFlags;
```

## <a name="ccomenumimplnext"></a><a name="next"></a>CComEnumimpl::下一個

此方法提供**Next**方法的實現。

```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```

### <a name="parameters"></a>參數

*celt*<br/>
[在]請求的元素數。

*格爾特*<br/>
[出]要填充的元素的陣列。

*pceltFetched*<br/>
[出]在*rgelt*中實際返回的元素數。 如果清單中保留的小於*celt*元素,則這可能小於*celt。*

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="ccomenumimplreset"></a><a name="reset"></a>CComEnumimpl::重置

此方法提供**重置**方法的實現。

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="ccomenumimplskip"></a><a name="skip"></a>CComEnumimpl::跳過

此方法提供**Skip**方法的實現。

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>參數

*celt*<br/>
[在]要跳過的元素數。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

如果*celt*為零,則返回E_INVALIDARG,如果返回小於*celt*元素,則返回S_FALSE返回,否則返回S_OK。

## <a name="see-also"></a>另請參閱

[IEnumonSTLimpl 類別](../../atl/reference/ienumonstlimpl-class.md)<br/>
[CComEnum 類別](../../atl/reference/ccomenum-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
