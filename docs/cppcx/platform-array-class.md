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
ms.openlocfilehash: d625d80df67a3c8207467ad629afd4c2bf88db18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318661"
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

平臺::Array從平台繼承其所有方法[::WriteOnlyArray類](../cppcx/platform-writeonlyarray-class.md)`Value`,實現[平台的屬性:::iBoxArray介面](../cppcx/platform-iboxarray-interface.md)。

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[Array 建構函式](#ctor)|初始化類範本參數*T*指定的一維、可修改的類型陣列。|

### <a name="methods"></a>方法

請參閱[平台::編寫「只寫陣列」 類別](../cppcx/platform-writeonlyarray-class.md)。

### <a name="properties"></a>屬性

|||
|-|-|
|[陣列:值](#value)|擷取目前陣列的控制代碼。|

### <a name="remarks"></a>備註

Array 類別已密封，無法被繼承。

Windows 運行時類型系統不支援鋸齒陣列的概念,因此不能將IVector<Platform::array\<T>> 作为返回值或方法参数传递。 若要跨 ABI 傳遞不規則陣列或一組序列中的某個序列，請使用 `IVector<IVector<T>^>`。

有關何時以及如何使用 Platform::Array 的詳細資訊,請參閱[陣列和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。

此類別定義於編譯器會自動納入的 vccorlib.h 標頭中。 它在 IntelliSense 中可見,但在物件瀏覽器中不可見,因為它不是在 platform.winmd 中定義的公共類型。

### <a name="requirements"></a>需求

編譯器選項: **/ZW**

## <a name="array-constructors"></a><a name="ctor"></a>陣列建構函式

初始化類範本參數*T*指定的一維、可修改的類型陣列。

## <a name="syntax"></a>語法

```cpp
Array(unsigned int size);
Array(T* data, unsigned int size);
```

#### <a name="parameters"></a>參數

*T*<br/>
類別樣板參數。

*大小*<br/>
陣列中的項目數。

*資料*<br/>
用來初始化此 Array 物件的 `T` 類型資料陣列的指標。

### <a name="remarks"></a>備註

有關如何建立平台實例的詳細資訊:陣列,請參閱[陣列和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。

## <a name="arrayget-method"></a><a name="get"></a>陣列::取得方法

在指定的索引位置擷取對陣列元素的參考。

## <a name="syntax"></a>語法

```cpp
T& get(unsigned int index)  const;
```

#### <a name="parameters"></a>參數

*指數*<br/>
識別陣列中元素的以零起始索引。 最小索引為 0,最大值索引`size`是[數位構造函數](#ctor)中參數指定的值。

### <a name="return-value"></a>傳回值

`index` 參數所指定的陣列元素。

## <a name="arrayvalue-property"></a><a name="value"></a>陣列:值屬性

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
