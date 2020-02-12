---
title: sampler 類別
ms.date: 06/28/2018
f1_keywords:
- sampler
- AMP_GRAPHICS/sampler
- AMP_GRAPHICS/concurrency::sampler::graphics::sampler
- AMP_GRAPHICS/concurrency::sampler::graphics::get_address_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::get_border_color
- AMP_GRAPHICS/concurrency::sampler::graphics::get_filter_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::address_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::border_color
- AMP_GRAPHICS/concurrency::sampler::graphics::filter_mode
ms.assetid: 9a6a9807-497d-402d-b092-8c4d86275b80
ms.openlocfilehash: 8f47bf6e9b88dba1e94e9e2ed2b93c8d2d3f9b8c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126345"
---
# <a name="sampler-class"></a>sampler 類別

取樣器類別會匯總要用於材質取樣的取樣設定資訊。

## <a name="syntax"></a>語法

```cpp
class sampler;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[取樣器的構造函式](#ctor)|已多載。 構造取樣器實例。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get_address_mode](#get_address_mode)|傳回與取樣器物件相關聯的 `address_mode`。|
|[get_border_color](#get_border_color)|傳回與取樣器物件相關聯的框線色彩。|
|[get_filter_mode](#get_filter_mode)|傳回與取樣器物件相關聯的 `filter_mode`。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator=](#operator_eq)|已多載。 指派運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[address_mode](#address_mode)|取得 `sampler` 物件的位址模式。|
|[border_color](#border_color)|取得 `sampler` 物件的框線色彩。|
|[filter_mode](#filter_mode)|取得 `sampler` 物件的篩選模式。|

## <a name="inheritance-hierarchy"></a>繼承階層

`sampler`

## <a name="requirements"></a>需求

**標頭：** amp_graphics。h

**命名空間：** concurrency：： graphics

## <a name="ctor"></a>採樣

構造[取樣器類別](sampler-class.md)的實例。

```cpp
sampler() restrict(cpu);    // [1] default constructor

sampler(                    // [2] constructor
    filter_mode _Filter_mode) restrict(cpu);

sampler(                    // [3] constructor
    address_mode _Address_mode,
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

sampler(                    // [4] constructor
    filter_mode _Filter_mode,
    address_mode _Address_mode,
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

sampler(                    // [5] copy constructor
    const sampler& _Other) restrict(amp,
    cpu);

sampler(                    // [6] move constructor
    sampler&& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>參數

*_Filter_mode*<br/>
要在取樣中使用的篩選模式。

*_Address_mode*<br/>
用於取樣所有維度的定址模式。

*_Border_color*<br/>
當地址模式 address_border 時，所要使用的框線色彩。 預設值是 `float_4(0.0f, 0.0f, 0.0f, 0.0f)`。

*_Other*<br/>
[5] 複製 `sampler` 要複製到新 `sampler` 實例的物件。

[6] 將 `sampler` 物件移動到新的 `sampler` 實例。

## <a name="address_mode"></a>address_mode

取得 `sampler` 物件的位址模式。

```cpp
__declspec(property(get= get_address_mode)) Concurrency::graphics::address_mode address_mode;
```

## <a name="border_color"></a>border_color

取得 `sampler` 物件的框線色彩。

```cpp
__declspec(property(get= get_border_color)) Concurrency::graphics::float_4 border_color;
```

## <a name="filter_mode"></a>filter_mode

取得 `sampler` 物件的篩選模式。

```cpp
__declspec(property(get= get_filter_mode)) Concurrency::graphics::filter_mode filter_mode;
```

## <a name="get_address_mode"></a>get_address_mode

傳回針對此 `sampler`所設定的篩選模式。

```cpp
Concurrency::graphics::address_mode get_address_mode() const __GPU;
```

### <a name="return-value"></a>傳回值

為取樣器設定的位址模式。

## <a name="get_border_color"></a>get_border_color

傳回針對此 `sampler`所設定的框線色彩。

```cpp
Concurrency::graphics::float_4 get_border_color() const restrict(amp, cpu);
```

### <a name="return-value"></a>傳回值

包含框線色彩的 float_4。

## <a name="get_filter_mode"></a>get_filter_mode

傳回針對此 `sampler`所設定的篩選模式。

```cpp
Concurrency::graphics::filter_mode get_filter_mode() const restrict(amp, cpu);
```

### <a name="return-value"></a>傳回值

針對取樣器所設定的篩選模式。

## <a name="operator_eq"></a>operator =

將另一個取樣器物件的值指派給現有的取樣器。

```cpp
sampler& operator= (    // [1] copy assignment operator
    const sampler& _Other) restrict(amp, cpu);

sampler& operator= (    // [2] move assignment operator
    sampler&& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>參數

*_Other*<br/>
[1] 複製指派運算子 `sampler` 要複製到這個 `sampler`的物件。

[2] 移動指派運算子 `sampler` 物件以移入這個 `sampler`。

### <a name="return-value"></a>傳回值

這個取樣器實例的參考。

## <a name="see-also"></a>另請參閱

[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)
