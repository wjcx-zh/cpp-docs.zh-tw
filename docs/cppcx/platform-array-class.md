---
title: Platform::Array 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Array Constructors
- VCCORLIB/Namespace not found::Platform::Array::Value
helpviewer_keywords:
- Platform::Array Class
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
ms.openlocfilehash: 94166dfcb222d5cfece146e7ad67bb04d6ad06e9
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221834"
---
# <a name="platformarray-class"></a>Platform::Array 類別

表示可修改的一維陣列，可在不同的應用程式二進位介面 (ABI) 之間接收和傳遞。

## <a name="syntax"></a>語法

```cpp
template <typename T>
private ref class Array<TArg, 1> :
    public WriteOnlyArray<TArg, 1>,
    public IBoxArray<TArg>
```

### <a name="members"></a>成員

Platform:: array 會繼承其所有方法從[platform:: writeonlyarray 類別](../cppcx/platform-writeonlyarray-class.md)，並會實作`Value`屬性[platform:: iboxarray 介面](../cppcx/platform-iboxarray-interface.md)。

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[Array 建構函式](#ctor)|初始化的一維陣列可修改的類別範本參數所指定的型別*T*。|

### <a name="methods"></a>方法

請參閱[platform:: writeonlyarray 類別](../cppcx/platform-writeonlyarray-class.md)。

### <a name="properties"></a>屬性

|||
|-|-|
|[Array::Value](#value)|擷取目前陣列的控制代碼。|

### <a name="remarks"></a>備註

Array 類別已密封，無法被繼承。

Windows 執行階段類型系統不支援不規則陣列的概念，因此您不能傳遞 Ivector<platform < platform:: array\<T >> 做為傳回的值或方法參數。 若要跨 ABI 傳遞不規則陣列或一組序列中的某個序列，請使用 `IVector<IVector<T>^>`。

如需何時及如何使用 platform:: array 的詳細資訊，請參閱[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。

此類別定義於編譯器會自動納入的 vccorlib.h 標頭中。 因為它不是 platform.winmd 中所定義的公用型別，它會顯示在 IntelliSense，但不是在物件瀏覽器。

### <a name="requirements"></a>需求

編譯器選項： **/ZW**

## <a name="ctor"></a>  Array 建構函式

初始化的一維陣列可修改的類別範本參數所指定的型別*T*。

## <a name="syntax"></a>語法

```cpp
Array(unsigned int size);
Array(T* data, unsigned int size);
```

#### <a name="parameters"></a>參數

*T*<br/>
類別樣板參數。

*size*<br/>
陣列中的項目數。

*data*<br/>
用來初始化此 Array 物件的 `T` 類型資料陣列的指標。

### <a name="remarks"></a>備註

如需如何建立 platform:: array 的執行個體的詳細資訊，請參閱[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。

## <a name="get"></a>  Array:: get 方法

在指定的索引位置擷取對陣列元素的參考。

## <a name="syntax"></a>語法

```cpp
T& get(unsigned int index)  const;
```

#### <a name="parameters"></a>參數

*index*<br/>
識別陣列中元素的以零起始索引。 最小的索引為 0，最大索引為所指定的值`size`中的參數[Array 建構函式](#ctor)。

### <a name="return-value"></a>傳回值

`index` 參數所指定的陣列元素。

## <a name="value"></a>  Array:: value 屬性

擷取目前陣列的控制代碼。

## <a name="syntax"></a>語法

```cpp
property Array^ Value;
```

### <a name="return-value"></a>傳回值

目前陣列的控制代碼。

## <a name="see-also"></a>另請參閱

[平台命名空間](../cppcx/platform-namespace-c-cx.md)<br/>
[Array 與 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
