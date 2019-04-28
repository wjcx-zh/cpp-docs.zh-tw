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
ms.openlocfilehash: 1a66e4d025a7592b78839dbe5f25f9103da41224
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352589"
---
# <a name="sampler-class"></a>sampler 類別

取樣器類別會彙總要用於材質取樣的取樣組態資訊。

## <a name="syntax"></a>語法

```cpp
class sampler;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[取樣器建構函式](#ctor)|多載。 建構取樣器執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get_address_mode](#get_address_mode)|傳回`address_mode`與取樣器物件相關聯。|
|[get_border_color](#get_border_color)|傳回與取樣器物件相關聯的框線色彩。|
|[get_filter_mode](#get_filter_mode)|傳回`filter_mode`與取樣器物件相關聯。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator=](#operator_eq)|多載。 指派運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[address_mode](#address_mode)|取得的位址模式`sampler`物件。|
|[border_color](#border_color)|取得框線色彩的`sampler`物件。|
|[filter_mode](#filter_mode)|取得篩選條件模式`sampler`物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`sampler`

## <a name="requirements"></a>需求

**標頭：** amp_graphics.h

**命名空間：** concurrency:: graphics

##  <a name="ctor"></a> 取樣器

建構的執行個體[sampler 類別](sampler-class.md)。

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
要用於取樣的篩選模式。

*_Address_mode*<br/>
要用於所有維度取樣的定址模式。

*_Border_color*<br/>
如果位址模式是 address_border，則會使用框線色彩。 預設值為 `float_4(0.0f, 0.0f, 0.0f, 0.0f)`。

*_Other*<br/>
[5] 複製建構函式`sampler`要複製到新物件`sampler`執行個體。

[6] 移動建構函式`sampler`移動到新物件`sampler`執行個體。

##  <a name="address_mode"></a> address_mode

取得的位址模式`sampler`物件。

```cpp
__declspec(property(get= get_address_mode)) Concurrency::graphics::address_mode address_mode;
```

##  <a name="border_color"></a> border_color

取得框線色彩的`sampler`物件。

```cpp
__declspec(property(get= get_border_color)) Concurrency::graphics::float_4 border_color;
```

##  <a name="filter_mode"></a> filter_mode

取得篩選條件模式`sampler`物件。

```cpp
__declspec(property(get= get_filter_mode)) Concurrency::graphics::filter_mode filter_mode;
```

##  <a name="get_address_mode"></a> get_address_mode

傳回這個已設定的篩選模式`sampler`。

```cpp
Concurrency::graphics::address_mode get_address_mode() const __GPU;
```

### <a name="return-value"></a>傳回值

設定取樣位址模式。

##  <a name="get_border_color"></a> get_border_color

傳回這個已設定的框線色彩`sampler`。

```cpp
Concurrency::graphics::float_4 get_border_color() const restrict(amp, cpu);
```

### <a name="return-value"></a>傳回值

包含框線色彩的 float_4。

##  <a name="get_filter_mode"></a> get_filter_mode

傳回這個已設定的篩選模式`sampler`。

```cpp
Concurrency::graphics::filter_mode get_filter_mode() const restrict(amp, cpu);
```

### <a name="return-value"></a>傳回值

取樣設定篩選模式。

##  <a name="operator_eq"></a> 運算子 =

將另一個的取樣器物件的值指派給現有取樣器中。

```cpp
sampler& operator= (    // [1] copy assignment operator
    const sampler& _Other) restrict(amp, cpu);

sampler& operator= (    // [2] move assignment operator
    sampler&& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>參數

*_Other*<br/>
[1] 複製指派運算子`sampler`要複製到這個物件`sampler`。

[2] 移動指派運算子`sampler`移動到這個物件`sampler`。

### <a name="return-value"></a>傳回值

此取樣器執行個體的參考。

## <a name="see-also"></a>另請參閱

[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)
