---
title: writeonly_texture_view 類別
ms.date: 11/04/2016
f1_keywords:
- writeonly_texture_view
- AMP_GRAPHICS/writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::rank Constant
ms.assetid: 8d117ad3-0a1c-41ae-b29c-7c95fdd4d04d
ms.openlocfilehash: 8978a548ed246c59d7e7f007f1180685c7343a14
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126236"
---
# <a name="writeonly_texture_view-class"></a>writeonly_texture_view 類別

提供材質的 writeonly 存取權。

## <a name="syntax"></a>語法

```cpp
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

### <a name="parameters"></a>參數

*value_type*<br/>
材質中元素的類型。

*_Rank*<br/>
材質的順位。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`scalar_type`||
|`value_type`|材質中元素的類型。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[writeonly_texture_view 的構造函式](#ctor)|初始化 `writeonly_texture_view` 類別的新執行個體。|
|[~ writeonly_texture_view 的析構函式](#ctor)|終結 `writeonly_texture_view` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[set](#set)|設定指定索引處的元素值。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator=](#operator_eq)|將指定的 `writeonly_texture_view` 物件複製到這個。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[次序常數](#rank)|取得 `writeonly_texture_view` 物件的順位。|

## <a name="inheritance-hierarchy"></a>繼承階層

`_Texture_base`

`writeonly_texture_view`

## <a name="requirements"></a>需求

**標頭：** amp_graphics。h

**命名空間：** Concurrency：： graphics

## <a name="dtor"></a>~ writeonly_texture_view

終結 `writeonly_texture_view` 物件。

```cpp
~writeonly_texture_view() restrict(amp,cpu);
```

## <a name="operator_eq"></a>operator =

將指定的 `writeonly_texture_view` 物件複製到這個。

```cpp
writeonly_texture_view<value_type, _Rank>& operator= (
    const writeonly_texture_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Other*<br/>
要複製的 `writeonly_texture_view` 物件。

### <a name="return-value"></a>傳回值

這個 `writeonly_texture_view` 物件的參考。

## <a name="rank"></a>等級

取得 `writeonly_texture_view` 物件的順位。

```cpp
static const int rank = _Rank;
```

## <a name="set"></a>設定

設定指定索引處的元素值。

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>參數

*_Index*<br/>
項目的索引。

*value*<br/>
項目的新值。

## <a name="ctor"></a>writeonly_texture_view

初始化 `writeonly_texture_view` 類別的新執行個體。

```cpp
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
材質中元素的類型。

*_Src*<br/>
用來建立 `writeonly_texture_view`的材質。

## <a name="see-also"></a>另請參閱

[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)
