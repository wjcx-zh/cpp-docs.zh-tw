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
ms.openlocfilehash: 7cf777f3ff0d298f224157735a06bf57a2c10cf5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495865"
---
# <a name="ienumonstlimpl-class"></a>IEnumOnSTLImpl 類別

這個類別會定義以C++標準程式庫集合為基礎的列舉值介面。

## <a name="syntax"></a>語法

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```

#### <a name="parameters"></a>參數

*群體*<br/>
COM 列舉值。 如需範例, 請參閱[IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) 。

*piid*<br/>
列舉值介面的介面識別碼指標。

*T*<br/>
列舉值介面所公開的專案類型。

*[複製]*<br/>
[複製原則類別](../../atl/atl-copy-policy-classes.md)。

*CollType*<br/>
C++標準程式庫容器類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IEnumOnSTLImpl::Clone](#clone)|**複製**的執行。|
|[IEnumOnSTLImpl::Init](#init)|初始化列舉程式。|
|[IEnumOnSTLImpl::Next](#next)|**下一個**的執行。|
|[IEnumOnSTLImpl::Reset](#reset)|**重設**的執行。|
|[IEnumOnSTLImpl::Skip](#skip)|**Skip**的執行。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[IEnumOnSTLImpl::m_iter](#m_iter)|反覆運算器, 表示列舉值在集合內的目前位置。|
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|C++標準程式庫容器的指標, 其中包含要列舉的專案。|
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|提供集合之物件的指標。`IUnknown`|

## <a name="remarks"></a>備註

`IEnumOnSTLImpl`提供 COM 列舉值介面的執行, 其中列舉的專案會儲存在C++標準程式庫相容的容器中。 這個類別類似于[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)類別, 它會針對以陣列為基礎的列舉值介面提供執行。

> [!NOTE]
>  如需和之間`CComEnumImpl`進一步差異的詳細資訊, `IEnumOnSTLImpl`請參閱[CComEnumImpl:: Init](../../atl/reference/ccomenumimpl-class.md#init) 。

一般來說, 您*不*需要藉由衍生自這個介面實來建立自己的列舉值類別。 如果您想要使用以C++標準程式庫容器為基礎的 ATL 提供的列舉值, 建立[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)的實例, 或建立可透過衍生自[ICollectionOnSTLImpl 來傳回枚舉器的集合類別, 是比較常見的方式](../../atl/reference/icollectiononstlimpl-class.md)。

不過, 如果您需要提供自訂列舉值 (例如, 除了列舉值介面外, 還會公開介面), 您可以從這個類別衍生。 在此情況下, 您可能需要覆寫[Clone](#clone)方法, 以提供您自己的執行。

## <a name="inheritance-hierarchy"></a>繼承階層

`Base`

`IEnumOnSTLImpl`

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

##  <a name="init"></a>IEnumOnSTLImpl:: Init

初始化列舉程式。

```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```

### <a name="parameters"></a>參數

*pUnkForRelease*<br/>
在物件`IUnknown`的指標, 必須在列舉值的存留期間保持作用中狀態。 如果沒有這類物件存在, 則傳遞 Null。

*collection*<br/>
C++標準程式庫容器的參考, 其中包含要列舉的專案。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

如果您將`Init`參考傳遞至保留在另一個物件中的集合, 則可以使用*pUnkForRelease*參數, 以確保只要列舉值需要, 它就會提供物件及其保存的集合。

您必須先呼叫這個方法, 然後再將列舉值介面的指標傳回給任何用戶端。

##  <a name="clone"></a>IEnumOnSTLImpl:: Clone

這個方法會藉由建立類型 `CComEnumOnSTL`的物件、使用目前物件所使用的相同集合和反覆運算器將其初始化, 並在新建立的物件上傳回介面, 來提供複製方法的執行。

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>參數

*ppEnum*<br/>
脫銷從目前列舉值複製的新建立物件上的列舉值介面。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="m_spunk"></a>IEnumOnSTLImpl::m_spUnk

提供集合之物件的指標。`IUnknown`

```
CComPtr<IUnknown> m_spUnk;
```

### <a name="remarks"></a>備註

這個智慧型指標會在傳遞給[IEnumOnSTLImpl:: Init](#init)的物件上維護參考, 以確保它在列舉值的存留期間保持運作狀態。

##  <a name="m_pcollection"></a>IEnumOnSTLImpl::m_pcollection

這個成員會指向提供資料的集合, 以驅動枚舉器介面的執行。

```
CollType* m_pcollection;
```

### <a name="remarks"></a>備註

這個成員是藉由呼叫[IEnumOnSTLImpl:: Init](#init)來初始化。

##  <a name="m_iter"></a>IEnumOnSTLImpl::m_iter

這個成員會保存反覆運算器, 用來標記集合中目前的位置, 並導覽至後續的元素。

```
CollType::iterator m_iter;
```

##  <a name="next"></a>IEnumOnSTLImpl:: Next

這個方法會提供**下一個**方法的執行。

```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```

### <a name="parameters"></a>參數

*celt*<br/>
在要求的元素數目。

*rgelt*<br/>
脫銷要填入元素的陣列。

*pceltFetched*<br/>
脫銷在*rgelt*中實際傳回的元素數目。 如果清單中保留的元素少於*celt* , 則此項可能小於*celt* 。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="reset"></a>IEnumOnSTLImpl:: Reset

這個方法會提供**Reset**方法的執行。

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="skip"></a>IEnumOnSTLImpl:: Skip

這個方法會提供**Skip**方法的實作為。

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>參數

*celt*<br/>
在要略過的元素數目。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)
