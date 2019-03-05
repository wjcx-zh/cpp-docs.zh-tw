---
title: IEnumOnSTLImpl 類別
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
ms.openlocfilehash: 8ff29522351b542d0b674bc173040d4468d00f1c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277442"
---
# <a name="ienumonstlimpl-class"></a>IEnumOnSTLImpl 類別

這個類別會定義根據 c + + 標準程式庫集合的列舉值介面。

## <a name="syntax"></a>語法

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```

#### <a name="parameters"></a>參數

*基底*<br/>
COM 列舉值。 請參閱[IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring)的範例。

*piid*<br/>
指標的列舉值介面的介面 ID。

*T*<br/>
列舉值介面所公開的項目類型。

*複製*<br/>
A[複製原則類別](../../atl/atl-copy-policy-classes.md)。

*CollType*<br/>
C + + 標準程式庫容器類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IEnumOnSTLImpl::Clone](#clone)|實作**複製品**。|
|[IEnumOnSTLImpl::Init](#init)|初始化列舉程式。|
|[IEnumOnSTLImpl::Next](#next)|實作**下一步**。|
|[IEnumOnSTLImpl::Reset](#reset)|實作**重設**。|
|[IEnumOnSTLImpl::Skip](#skip)|實作**略過**。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[IEnumOnSTLImpl::m_iter](#m_iter)|迭代器，表示集合中的列舉值的目前位置。|
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|C + + 標準程式庫容器保存要列舉項目的指標。|
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|`IUnknown`提供集合之物件的指標。|

## <a name="remarks"></a>備註

`IEnumOnSTLImpl` 提供 c + + 標準程式庫相容的容器中儲存所列舉之項目的 COM 列舉程式介面的實作。 這個類別是類似[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)陣列為基礎的類別，可提供列舉值介面的實作。

> [!NOTE]
>  請參閱[CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init)如需有關進一步之間的差異`CComEnumImpl`和`IEnumOnSTLImpl`。

一般而言，您將會*不*需要建立自己的列舉值類別，藉由衍生自這個介面實作。 如果您想要使用 c + + 標準程式庫容器為基礎的 ATL 提供列舉值，是要建立的執行個體更常見[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)，或建立集合類別，傳回的列舉值，藉由衍生自[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)。

不過，如果您需要提供自訂的列舉值 （例如，一個公開除了列舉程式介面的介面），您可以衍生自這個類別。 在此情況下很有可能，您必須覆寫[複製品](#clone)方法，以提供您自己的實作。

## <a name="inheritance-hierarchy"></a>繼承階層

`Base`

`IEnumOnSTLImpl`

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="init"></a>  IEnumOnSTLImpl::Init

初始化列舉程式。

```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```

### <a name="parameters"></a>參數

*pUnkForRelease*<br/>
[in]`IUnknown`必須保持運作的存留期間列舉值物件的指標。 如果物件不存在，請傳遞 NULL。

*collection*<br/>
包含要列舉的項目 c + + 標準程式庫容器的參考。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

如果您傳遞`Init`集合的參考保留在另一個物件，您可以使用*pUnkForRelease*參數，確保，物件和集合當中，僅適用於只要列舉值需要它。

您必須先呼叫這個方法，才能將指標傳遞給任何用戶端的列舉值介面。

##  <a name="clone"></a>  IEnumOnSTLImpl::Clone

這個方法提供實作**複製品**方法，藉由建立型別的物件`CComEnumOnSTL`，初始化具有相同的集合與目前物件所使用的迭代器，並傳回介面新建立的物件。

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>參數

*ppEnum*<br/>
[out]從目前的列舉值，複製新建立的物件上的列舉值介面。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="m_spunk"></a>  IEnumOnSTLImpl::m_spUnk

`IUnknown`提供集合之物件的指標。

```
CComPtr<IUnknown> m_spUnk;
```

### <a name="remarks"></a>備註

這個智慧型指標會維持對傳遞至的物件參考[IEnumOnSTLImpl::Init](#init)，確保它仍然保持運作的列舉值的存留期間。

##  <a name="m_pcollection"></a>  IEnumOnSTLImpl::m_pcollection

這個成員會指向集合提供資料驅動的列舉值介面的實作。

```
CollType* m_pcollection;
```

### <a name="remarks"></a>備註

此成員已初始化的呼叫所[IEnumOnSTLImpl::Init](#init)。

##  <a name="m_iter"></a>  IEnumOnSTLImpl::m_iter

這個成員保留迭代器，用來將標記在集合中目前的位置，並瀏覽至後續項目。

```
CollType::iterator m_iter;
```

##  <a name="next"></a>  IEnumOnSTLImpl::Next

這個方法可實作**下一步**方法。

```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```

### <a name="parameters"></a>參數

*celt*<br/>
[in]要求的元素數目。

*rgelt*<br/>
[out]要填入之項目的陣列。

*pceltFetched*<br/>
[out]中實際傳回項目數*rgelt*。 這可以是小於*celt*如果少於*celt*仍然在清單中的項目。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="reset"></a>  IEnumOnSTLImpl::Reset

這個方法可實作**重設**方法。

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="skip"></a>  IEnumOnSTLImpl::Skip

這個方法可實作**略過**方法。

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>參數

*celt*<br/>
[in]略過的項目數目。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
