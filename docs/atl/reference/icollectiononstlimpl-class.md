---
title: ICollectionOnSTLImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl::get__NewEnum
- ATLCOM/ATL::ICollectionOnSTLImpl::getcount
- ATLCOM/ATL::ICollectionOnSTLImpl::get_Item
- ATLCOM/ATL::ICollectionOnSTLImpl::m_coll
dev_langs:
- C++
helpviewer_keywords:
- ICollectionOnSTLImpl class
ms.assetid: 683c88b0-0d97-4779-a762-e493334ba7f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2b70e7332c5f0a24af80ddb5cfd14a8ecf146de
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025148"
---
# <a name="icollectiononstlimpl-class"></a>ICollectionOnSTLImpl 類別

這個類別提供的集合類別所使用的方法。

## <a name="syntax"></a>語法

```
template <class T, class CollType, class ItemType, class CopyItem, class EnumType>
class ICollectionOnSTLImpl : public T
```

#### <a name="parameters"></a>參數

*T*<br/>
COM 集合介面。

*CollType*<br/>
C + + 標準程式庫容器類別。

*ItemType*<br/>
容器介面所公開的項目類型。

*CopyItem*<br/>
A[複製原則類別](../../atl/atl-copy-policy-classes.md)。

*EnumType*<br/>
A [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)-相容的列舉值類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[ICollectionOnSTLImpl::get__NewEnum](#newenum)|傳回集合的列舉值物件。|
|[ICollectionOnSTLImpl::getcount](#get_count)|傳回集合中的項目數目。|
|[ICollectionOnSTLImpl::get_Item](#get_item)|從集合中傳回要求的項目。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[ICollectionOnSTLImpl::m_coll](#m_coll)|集合。|

## <a name="remarks"></a>備註

這個類別會提供三種方法的集合介面的實作： [getcount](#get_count)， [get_Item](#get_item)，並[get__NewEnum](#newenum)。

若要使用此類別：

- 定義 （或借用） 您想要實作集合介面。

- 衍生類別的特製化從`ICollectionOnSTLImpl`根據此集合介面。

- 使用您的衍生的類別來實作任何方法，從集合介面並非由`ICollectionOnSTLImpl`。

> [!NOTE]
>  如果集合介面是雙重介面，衍生您的類別，從[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)，並傳遞`ICollectionOnSTLImpl`如果您想要提供的實作的 ATL 的第一個範本參數的特製化`IDispatch`方法。

- 將項目加入[m_coll](#m_coll)来填入集合的成員。

如需詳細資訊和範例，請參閱 < [ATL 集合和列舉程式](../../atl/atl-collections-and-enumerators.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`T`

`ICollectionOnSTLImpl`

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="get_count"></a>  ICollectionOnSTLImpl::getcount

這個方法會傳回集合中的項目數。

```
STDMETHOD(getcount)(long* pcount);
```

### <a name="parameters"></a>參數

*pcount*<br/>
[out]集合中的項目數目。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="get_item"></a>  ICollectionOnSTLImpl::get_Item

這個方法會傳回集合中指定的項目。

```
STDMETHOD(get_Item)(long Index, ItemType* pvar);
```

### <a name="parameters"></a>參數

*Tuple*<br/>
[in]集合中的項目 1 為基底的索引。

*pvar*<br/>
[out]對應至的項目*Index*。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

藉由複製的資料中指定的位置取得項目[m_coll](#m_coll)使用的複製方法[複製原則類別](../../atl/atl-copy-policy-classes.md)作為範本引數中傳遞`ICollectionOnSTLImpl`特製化。

##  <a name="newenum"></a>  ICollectionOnSTLImpl::get__NewEnum

傳回集合的列舉值物件。

```
STDMETHOD(get__NewEnum)(IUnknown** ppUnk);
```

### <a name="parameters"></a>參數

*ppUnk*<br/>
[out]**IUnknown**新建立列舉值物件的指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

新建立的列舉值會維持在原始集合中，迭代器`m_coll`（因此會不製作任何複本），以確保集合保持運作的雖然有未處理的列舉值的集合物件上保留的 COM 參考。

##  <a name="m_coll"></a>  ICollectionOnSTLImpl::m_coll

此成員會包含集合所代表的項目。

```
CollType m_coll;
```

## <a name="see-also"></a>另請參閱

[ATLCollections 範例](../../visual-cpp-samples.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
