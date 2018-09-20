---
title: writeonly_texture_view 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- writeonly_texture_view
- AMP_GRAPHICS/writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::rank Constant
dev_langs:
- C++
ms.assetid: 8d117ad3-0a1c-41ae-b29c-7c95fdd4d04d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd92e403d9c83bf50bea2703cef6a4255c6245e3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414668"
---
# <a name="writeonlytextureview-class"></a>writeonly_texture_view 類別

提供 writeonly 存取材質。

## <a name="syntax"></a>語法

```
template <
    typename value_type,
    int _Rank
>
class writeonly_texture_view;

template <
    typename value_type,
    int _Rank
>
class writeonly_texture_view<value_type, _Rank> : public details::_Texture_base<value_type, _Rank>;
```

#### <a name="parameters"></a>參數

*value_type*<br/>
材質中項目的類型。

*_Rank*<br/>
材質的順位。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`scalar_type`||
|`value_type`|材質中項目的類型。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[writeonly_texture_view 建構函式](#ctor)|初始化 `writeonly_texture_view` 類別的新執行個體。|
|[~ writeonly_texture_view 解構函式](#ctor)|終結`writeonly_texture_view`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[set](#set)|指定索引處設定項目的值。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator=](#operator_eq)|複製指定`writeonly_texture_view`如下的物件。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[rank 常數](#rank)|取得的順位`writeonly_texture_view`物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`_Texture_base`

`writeonly_texture_view`

## <a name="requirements"></a>需求

**標頭：** amp_graphics.h

**命名空間：** concurrency:: graphics

##  <a name="dtor"></a> ~writeonly_texture_view

終結`writeonly_texture_view`物件。

```
~writeonly_texture_view() restrict(amp,cpu);
```

##  <a name="operator_eq"></a> 運算子 =

複製指定`writeonly_texture_view`如下的物件。

```
writeonly_texture_view<value_type, _Rank>& operator= (
    const writeonly_texture_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Other*<br/>
`writeonly_texture_view` 若要從複製的物件。

### <a name="return-value"></a>傳回值

此參考`writeonly_texture_view`物件。

##  <a name="rank"></a> 陣序規範

取得的順位`writeonly_texture_view`物件。

```
static const int rank = _Rank;
```

##  <a name="set"></a> 設定

指定索引處設定項目的值。

```
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>參數

*_Index*<br/>
項目的索引。

*值*<br/>
項目的新值。

##  <a name="ctor"></a> writeonly_texture_view

初始化 `writeonly_texture_view` 類別的新執行個體。

```
writeonly_texture_view(
    texture<value_type,
    _Rank>& _Src) restrict(amp);

writeonly_texture_view(
    const writeonly_texture_view<value_type,
    _Rank>& _Src) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Rank*<br/>
材質的順位。

*value_type*<br/>
材質中項目的類型。

*_Src*<br/>
用來建立紋理`writeonly_texture_view`。

## <a name="see-also"></a>另請參閱

[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)
