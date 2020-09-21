---
title: Platform::Array 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Array
- VCCORLIB/Platform::Array::Value
helpviewer_keywords:
- Platform::Array Class
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
ms.openlocfilehash: 4903c18f981c87c418a6ab08595816ce22a7413c
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742940"
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

Platform：： Array 會從 [platform：： WriteOnlyArray 類別](../cppcx/platform-writeonlyarray-class.md) 繼承其所有方法，並實作為 `Value` [Platform：： IBoxArray 介面](../cppcx/platform-iboxarray-interface.md)的屬性。

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[Array 建構函式](#ctor)|初始化類別樣板參數 *T*所指定之類型的一維可修改陣列。|

### <a name="methods"></a>方法

請參閱 [Platform：： WriteOnlyArray 類別](../cppcx/platform-writeonlyarray-class.md)。

### <a name="properties"></a>屬性

| 名稱 | 描述 |
|--|--|
| [Array：： Value](#value) | 擷取目前陣列的控制代碼。 |

### <a name="remarks"></a>備註

Array 類別已密封，無法被繼承。

Windows 執行階段類型系統不支援不規則陣列的概念，因此您無法傳遞 `IVector<Platform::Array<T>>` 做為傳回值或方法參數。 若要跨 ABI 傳遞不規則陣列或一組序列中的某個序列，請使用 `IVector<IVector<T>^>`。

如需有關何時及如何使用 Platform：： Array 的詳細資訊，請參閱 [Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。

此類別定義於編譯器會自動納入的 vccorlib.h 標頭中。 它會顯示在 IntelliSense 中，但不是在物件瀏覽器中，因為它不是在 platform 中定義的公用類型。

### <a name="requirements"></a>規格需求

編譯器選項： **/ZW**

## <a name="array-constructors"></a><a name="ctor"></a> 陣列的函式

初始化類別樣板參數 *T*所指定之類型的一維可修改陣列。

### <a name="syntax"></a>語法

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

如需如何建立 Platform：： Array 實例的詳細資訊，請參閱 [Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。

## <a name="arrayget-method"></a><a name="get"></a> Array：： get 方法

在指定的索引位置擷取對陣列元素的參考。

### <a name="syntax"></a>語法

```cpp
T& get(unsigned int index)  const;
```

#### <a name="parameters"></a>參數

*index*<br/>
識別陣列中元素的以零起始索引。 最小的索引是0，而最大的索引是陣列函式中參數所指定的值 `size` 。 [Array constructor](#ctor)

### <a name="return-value"></a>傳回值

`index` 參數所指定的陣列元素。

## <a name="arrayvalue-property"></a><a name="value"></a> Array：： Value 屬性

擷取目前陣列的控制代碼。

### <a name="syntax"></a>語法

```cpp
property Array^ Value;
```

### <a name="return-value"></a>傳回值

目前陣列的控制代碼。

## <a name="see-also"></a>另請參閱

[平台命名空間](../cppcx/platform-namespace-c-cx.md)<br/>
[Array 與 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
