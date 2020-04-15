---
title: CComQIPtr 元素類別
ms.date: 11/04/2016
f1_keywords:
- CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits::INARGTYPE
helpviewer_keywords:
- CComQIPtrElementTraits class
ms.assetid: 9df9250a-5413-4362-b133-332932a597c4
ms.openlocfilehash: 19f2669c157310be02f746672b22f6c0ed005075
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327402"
---
# <a name="ccomqiptrelementtraits-class"></a>CComQIPtr 元素類別

此類提供在創建 COM 介面指標集合時有用的方法、靜態函數和 typedef。

## <a name="syntax"></a>語法

```
template<typename I, const IID* piid=& __uuidof(I)>
class CComQIPtrElementTraits :
   public CDefaultElementTraits<ATL::CComQIPtr<I, piid>>
```

#### <a name="parameters"></a>參數

*I.*<br/>
指定要儲存的指標類型的 COM 介面。

*皮伊德*<br/>
指向*I*的 IID 的指標。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CComQIPtr元素::INARGTYPE](#inargtype)|用於向集合類物件添加元素的數據類型。|

## <a name="remarks"></a>備註

類派生方法並提供類型def,用於創建[CComQIPtr](../../atl/reference/ccomqiptr-class.md) COM介面指針對象的集合類。 [CInterfaceArray](../../atl/reference/cinterfacearray-class.md)和[CInterfaceList](../../atl/reference/cinterfacelist-class.md)類都使用此類。

有關詳細資訊,請參閱[ATL 收集類](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[C 預設比較特徵](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[元素庫](../../atl/reference/celementtraitsbase-class.md)

[CDefault 元素](../../atl/reference/cdefaultelementtraits-class.md)

`CComQIPtrElementTraits`

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="ccomqiptrelementtraitsinargtype"></a><a name="inargtype"></a>CComQIPtr元素::INARGTYPE

用於向集合類物件添加元素的數據類型。

```
typedef I* INARGTYPE;
```

## <a name="see-also"></a>另請參閱

[CDefaultElementtraits 類別](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
