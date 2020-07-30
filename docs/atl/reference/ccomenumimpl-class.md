---
title: CComEnumImpl 類別
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
ms.openlocfilehash: 517a4e90ca21e22dcf161aefcff61a40437eabe0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226603"
---
# <a name="ccomenumimpl-class"></a>CComEnumImpl 類別

這個類別會提供 COM 列舉值介面的實值，其中要列舉的專案會儲存在陣列中。

## <a name="syntax"></a>語法

```
template <class Base,
    const IID* piid, class T, class Copy>
class ATL_NO_VTABLE CComEnumImpl : public Base
```

#### <a name="parameters"></a>參數

*群體*<br/>
COM 列舉值介面。 如需範例，請參閱[IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) 。

*piid*<br/>
列舉值介面的介面識別碼指標。

*T*<br/>
列舉值介面所公開的專案類型。

*複製*<br/>
同質[複製原則類別](../../atl/atl-copy-policy-classes.md)。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|建構函式。|
|[CComEnumImpl：： ~ CComEnumImpl](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CComEnumImpl：： Clone](#clone)|**複製**列舉介面方法的執行。|
|[CComEnumImpl：： Init](#init)|初始化列舉程式。|
|[CComEnumImpl：： Next](#next)|**下一個**的執行。|
|[CComEnumImpl：： Reset](#reset)|**重設**的執行。|
|[CComEnumImpl：： Skip](#skip)|**Skip**的執行。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CComEnumImpl：： m_begin](#m_begin)|陣列中第一個專案的指標。|
|[CComEnumImpl：： m_dwFlags](#m_dwflags)|透過傳遞的複製旗標 `Init` 。|
|[CComEnumImpl：： m_end](#m_end)|陣列中最後一個專案之後的位置指標。|
|[CComEnumImpl：： m_iter](#m_iter)|陣列中目前專案的指標。|
|[CComEnumImpl：： m_spUnk](#m_spunk)|`IUnknown`提供要列舉之集合的物件指標。|

## <a name="remarks"></a>備註

如需方法實現的範例，請參閱[IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) 。 `CComEnumImpl`提供 COM 枚舉器介面的執行，其中列舉的專案會儲存在陣列中。 這個類別類似于 `IEnumOnSTLImpl` 類別，它會根據 c + + 標準程式庫容器來提供枚舉器介面的執行。

> [!NOTE]
> 如需和之間進一步差異的詳細資訊 `CComEnumImpl` `IEnumOnSTLImpl` ，請參閱[CComEnumImpl：： Init](#init)。

一般來說，您*不*需要藉由衍生自這個介面實來建立自己的列舉值類別。 如果您想要使用以陣列為基礎的 ATL 提供的列舉值，則建立[CComEnum](../../atl/reference/ccomenum-class.md)的實例較為常見。

不過，如果您需要提供自訂列舉值（例如，除了列舉值介面外，還會公開介面），您可以從這個類別衍生。 在此情況下，您可能需要覆寫[CComEnumImpl：： Clone](#clone)方法，以提供您自己的執行。

如需詳細資訊，請參閱[ATL 集合和枚舉](../../atl/atl-collections-and-enumerators.md)器。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Base`

`CComEnumImpl`

## <a name="requirements"></a>需求

**標頭：** atlcom.h。h

## <a name="ccomenumimplccomenumimpl"></a><a name="ccomenumimpl"></a>CComEnumImpl::CComEnumImpl

建構函式。

```
CComEnumImpl();
```

## <a name="ccomenumimplccomenumimpl"></a><a name="dtor"></a>CComEnumImpl：： ~ CComEnumImpl

解構函式。

```
~CComEnumImpl();
```

## <a name="ccomenumimplinit"></a><a name="init"></a>CComEnumImpl：： Init

您必須先呼叫這個方法，然後再將列舉值介面的指標傳回給任何用戶端。

```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```

### <a name="parameters"></a>參數

*起點*<br/>
陣列的第一個元素的指標，其中包含要列舉的專案。

*成品*<br/>
包含要列舉之專案之陣列最後一個元素之後的位置指標。

*pUnk*<br/>
在`IUnknown`物件的指標，必須在列舉值的存留期間保持作用中狀態。 如果沒有這類物件存在，則傳遞 Null。

*flags*<br/>
指定列舉值是否應取得陣列擁有權或建立其複本的旗標。 可能的值如下所述。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

只呼叫這個方法一次—初始化列舉值，使用它，然後將它擲回。

如果您將指標傳遞至保留在另一個物件中之陣列中的專案（而且您不會要求列舉值複製資料），您可以使用*pUnk*參數，以確保只要列舉值需要，物件和它所保留的陣列就能使用。 列舉值只會保存物件的 COM 參考，讓它保持在運作狀態。 當列舉值損毀時，會自動釋放 COM 參考。

*Flags*參數可讓您指定枚舉器應如何處理傳遞給它的陣列元素。 *旗標*可以接受列舉中的其中一個值， `CComEnumFlags` 如下所示：

```
enum CComEnumFlags
   {
   AtlFlagNoCopy = 0,
   AtlFlagTakeOwnership = 2, // BitOwn
   AtlFlagCopy = 3           // BitOwn | BitCopy
   };
```

`AtlFlagNoCopy`表示陣列的存留期不是由列舉值所控制。 在此情況下，陣列會是靜態的，或*pUnk*所識別的物件會負責在不再需要時釋放陣列。

`AtlFlagTakeOwnership`表示陣列的銷毀是由列舉值所控制。 在此情況下，必須使用動態配置陣列 **`new`** 。 列舉值會刪除其析構函式中的陣列。 一般來說，您會將 Null 傳遞給*pUnk*，不過，如果您因為某些原因而需要收到列舉值的通知，仍然可以傳遞有效的指標。

`AtlFlagCopy`表示要藉由複製傳遞至的陣列來建立新的陣列 `Init` 。 新陣列的存留期是由列舉值所控制。 列舉值會刪除其析構函式中的陣列。 一般來說，您會將 Null 傳遞給*pUnk*，不過，如果您因為某些原因而需要收到列舉值的通知，仍然可以傳遞有效的指標。

> [!NOTE]
> 這個方法的原型會將陣列元素指定為類型 `T` ，其中 `T` 已定義為類別的樣板參數。 這是透過 COM 介面方法[CComEnumImpl：： Next](#next)所公開的相同型別。 其含意是，與[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)不同的是，這個類別不支援不同的儲存體和公開的資料類型。 陣列中元素的資料類型必須與透過 COM 介面所公開的資料類型相同。

## <a name="ccomenumimplclone"></a><a name="clone"></a>CComEnumImpl：： Clone

這個方法會藉由建立類型**Clone**的物件 `CComEnum` 、使用目前物件所使用的相同陣列和反覆運算器將其初始化，並在新建立的物件上傳回介面，藉以提供複製方法的執行。

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>參數

*ppEnum*<br/>
脫銷從目前列舉值複製的新建立物件上的列舉值介面。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

請注意，複製的列舉值永遠不會為原始枚舉器所使用的資料建立自己的複本（或取得擁有權）。 如有需要，複製的列舉值會讓原始枚舉器保持運作（使用 COM 參考），以確保資料可以在需要時使用。

## <a name="ccomenumimplm_spunk"></a><a name="m_spunk"></a>CComEnumImpl：： m_spUnk

這個智慧型指標會在傳遞給[CComEnumImpl：： Init](#init)的物件上維護參考，以確保它在列舉值的存留期間保持運作狀態。

```
CComPtr<IUnknown> m_spUnk;
```

## <a name="ccomenumimplm_begin"></a><a name="m_begin"></a>CComEnumImpl：： m_begin

包含要列舉之專案之陣列最後一個元素之後的位置指標。

```
T* m_begin;
```

## <a name="ccomenumimplm_end"></a><a name="m_end"></a>CComEnumImpl：： m_end

陣列的第一個元素的指標，其中包含要列舉的專案。

```
T* m_end;
```

## <a name="ccomenumimplm_iter"></a><a name="m_iter"></a>CComEnumImpl：： m_iter

陣列目前元素的指標，其中包含要列舉的專案。

```
T* m_iter;
```

## <a name="ccomenumimplm_dwflags"></a><a name="m_dwflags"></a>CComEnumImpl：： m_dwFlags

傳遞至[CComEnumImpl：： Init](#init)的旗標。

```
DWORD m_dwFlags;
```

## <a name="ccomenumimplnext"></a><a name="next"></a>CComEnumImpl：： Next

這個方法會提供**下一個**方法的執行。

```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```

### <a name="parameters"></a>參數

*celt*<br/>
在要求的元素數目。

*rgelt*<br/>
脫銷要填入元素的陣列。

*pceltFetched*<br/>
脫銷在*rgelt*中實際傳回的元素數目。 如果清單中保留的元素少於*celt* ，這可能會小於*celt* 。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

## <a name="ccomenumimplreset"></a><a name="reset"></a>CComEnumImpl：： Reset

這個方法會提供**Reset**方法的執行。

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

## <a name="ccomenumimplskip"></a><a name="skip"></a>CComEnumImpl：： Skip

這個方法會提供**Skip**方法的實作為。

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>參數

*celt*<br/>
在要略過的元素數目。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

如果*celt*是零，則傳回 E_INVALIDARG，如果傳回的值小於*celt*的元素，則會傳回 S_FALSE 否則會傳回 S_OK。

## <a name="see-also"></a>另請參閱

[IEnumOnSTLImpl 類別](../../atl/reference/ienumonstlimpl-class.md)<br/>
[CComEnum 類別](../../atl/reference/ccomenum-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
