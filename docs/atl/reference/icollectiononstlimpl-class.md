---
title: ICollectiononSTLimpl 類別
ms.date: 11/04/2016
f1_keywords:
- ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl::get__NewEnum
- ATLCOM/ATL::ICollectionOnSTLImpl::getcount
- ATLCOM/ATL::ICollectionOnSTLImpl::get_Item
- ATLCOM/ATL::ICollectionOnSTLImpl::m_coll
helpviewer_keywords:
- ICollectionOnSTLImpl class
ms.assetid: 683c88b0-0d97-4779-a762-e493334ba7f9
ms.openlocfilehash: a8ccab08b89da8c1b8ef56c8932e27a6c74e62aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329900"
---
# <a name="icollectiononstlimpl-class"></a>ICollectiononSTLimpl 類別

此類提供集合類使用的方法。

## <a name="syntax"></a>語法

```
template <class T, class CollType, class ItemType, class CopyItem, class EnumType>
class ICollectionOnSTLImpl : public T
```

#### <a name="parameters"></a>參數

*T*<br/>
COM 集合介面。

*拼貼*<br/>
C++標準庫容器類。

*ItemType*<br/>
容器介面公開的項的類型。

*複製項目*<br/>
[複製原則類別](../../atl/atl-copy-policy-classes.md)。

*列舉類型*<br/>
[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)- 相容枚舉器類。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[ICollectiononSTLimpl::get__NewEnum](#newenum)|返回集合的枚舉物件。|
|[ICollectiononSTLimpl::取得計數](#get_count)|返回集合中的元素數。|
|[ICollectiononSTLimpl:get_Item](#get_item)|從集合返回請求的項。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[ICollectiononSTLimpl:m_coll](#m_coll)|集合。|

## <a name="remarks"></a>備註

此類為集合介面的三種方法提供實現[:getcount、get_Item](#get_count)和[get_Item](#get_item)[get__NewEnum](#newenum)。

要使用此類:

- 定義(或借用)要實現的集合介面。

- 基於此集合介面的`ICollectionOnSTLImpl`專門化派生類。

- 使用派生類實現來自 未`ICollectionOnSTLImpl`由 處理的集合介面的任何方法。

> [!NOTE]
> 如果集合介面是雙介面,請從[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)派生類,`ICollectionOnSTLImpl`如果希望`IDispatch`ATL 提供方法的實現,則將專業化作為第一個範本參數傳遞。

- 將項添加到[m_coll](#m_coll)成員以填充集合。

有關詳細資訊和範例,請參閱[ATL 集合和枚舉器](../../atl/atl-collections-and-enumerators.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`T`

`ICollectionOnSTLImpl`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="icollectiononstlimplgetcount"></a><a name="get_count"></a>ICollectiononSTLimpl::取得計數

此方法返回集合中的項數。

```
STDMETHOD(getcount)(long* pcount);
```

### <a name="parameters"></a>參數

*pcount*<br/>
[出]集合中的元素數。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="icollectiononstlimplget_item"></a><a name="get_item"></a>ICollectiononSTLimpl:get_Item

此方法從集合中返回指定的項。

```
STDMETHOD(get_Item)(long Index, ItemType* pvar);
```

### <a name="parameters"></a>參數

*索引*<br/>
[在]集合中項的基於 1 的索引。

*普瓦爾*<br/>
[出]對應於*索引*的項目 。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

通過使用在`ICollectionOnSTLImpl`專門化中作為範本參數傳遞[的複製策略類](../../atl/atl-copy-policy-classes.md)的複製方法,在[m_coll](#m_coll)的指定位置複製數據,從而獲取該專案。

## <a name="icollectiononstlimplget__newenum"></a><a name="newenum"></a>ICollectiononSTLimpl::get__NewEnum

返回集合的枚舉物件。

```
STDMETHOD(get__NewEnum)(IUnknown** ppUnk);
```

### <a name="parameters"></a>參數

*普恩克*<br/>
[出]新創建的枚舉器物件的**I 未知**指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

新創建的枚舉器在原始集合上維護反覆運算器`m_coll`(因此不創建副本),並在集合物件上保留 COM 引用,以確保集合在存在未完成的枚舉器時保持活動狀態。

## <a name="icollectiononstlimplm_coll"></a><a name="m_coll"></a>ICollectiononSTLimpl:m_coll

此成員保存集合表示的項。

```
CollType m_coll;
```

## <a name="see-also"></a>另請參閱

[ATL集合範例](../../overview/visual-cpp-samples.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
