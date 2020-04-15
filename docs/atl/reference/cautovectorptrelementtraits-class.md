---
title: CAutoVectorPtr 元素類別
ms.date: 11/04/2016
f1_keywords:
- CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoVectorPtrElementTraits class
ms.assetid: 16b81a56-55fb-46ca-b376-66a1884231a6
ms.openlocfilehash: 956fe39c4d3ba89bb9def2f996dca59905753edb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318748"
---
# <a name="cautovectorptrelementtraits-class"></a>CAutoVectorPtr 元素類別

此類提供使用向量新運算符和刪除運算符創建智慧指標集合時有用的方法、靜態函數和 typedef。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <typename T>
class CAutoVectorPtrElementTraits :
   public CDefaultElementTraits<ATL::CAutoVectorPtr<T>>
```

#### <a name="parameters"></a>參數

*T*<br/>
指標類型。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[C自動向量元素::INARGTYPE](#inargtype)|用於向集合類物件添加元素的數據類型。|
|[C自動向量元素::OUTARGTYPE](#outargtype)|用於從集合類物件檢索元素的數據類型。|

## <a name="remarks"></a>備註

此類提供用於幫助創建包含智慧指標的集合類物件的方法、靜態函數和 typedef。 與[CAutoPtrElementTraits 不同](../../atl/reference/cautoptrelementtraits-class.md),此類使用向量新運算元和刪除運算符。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[C 預設比較特徵](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[元素庫](../../atl/reference/celementtraitsbase-class.md)

[CDefault 元素](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoVectorPtrElementTraits`

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="cautovectorptrelementtraitsinargtype"></a><a name="inargtype"></a>C自動向量元素::INARGTYPE

用於向集合類物件添加元素的數據類型。

```
typedef CAutoVectorPtr<T>& INARGTYPE;
```

## <a name="cautovectorptrelementtraitsoutargtype"></a><a name="outargtype"></a>C自動向量元素::OUTARGTYPE

用於從集合類物件檢索元素的數據類型。

```
typedef T*& OUTARGTYPE;
```

## <a name="see-also"></a>另請參閱

[CDefaultElementtraits 類別](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[C 自動向量Ptr 類別](../../atl/reference/cautovectorptr-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
