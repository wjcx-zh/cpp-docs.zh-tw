---
title: Platform::WriteOnlyArray 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WriteOnlyArray::begin
- VCCORLIB/Platform::WriteOnlyArray::Data
- VCCORLIB/Platform::WriteOnlyArray::end
- VCCORLIB/Platform::WriteOnlyArray::FastPass
- VCCORLIB/Platform::WriteOnlyArray::Length
- VCCORLIB/Platform::WriteOnlyArray::set
helpviewer_keywords:
- Platform::WriteOnlyArray Class
ms.assetid: 92d7dd56-ec58-4b8c-88ba-9c903668b687
ms.openlocfilehash: d06ed19b7c041f9ae73f862ba521449a206aa321
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374651"
---
# <a name="platformwriteonlyarray-class"></a>Platform::WriteOnlyArray 類別

表示一維陣列。當呼叫端傳遞陣列讓方法填滿其中元素時，就會將這個陣列當做輸入參數來傳遞。

這個 ref 類別在 vccorlib.h 中是宣告為私用，因此不會在中繼資料內發出，而且只能從 C++ 使用。 這個類別只做為用來接收呼叫端所配置之陣列的輸入參數。 您無法從使用者程式碼建構這個類別。 它可以讓 C++ 方法直接在陣列中寫入資料，這就稱為「 *FillArray* 」模式。 有關詳細資訊,請參閱[陣列和寫入唯一陣列](../cppcx/array-and-writeonlyarray-c-cx.md)。

## <a name="syntax"></a>語法

```cpp
private ref class WriteOnlyArray<T, 1>
```

### <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

這些方法的存取範圍都是 internal，也就是說，您只能在 C++ 應用程式或元件內存取這些方法。

|名稱|描述|
|----------|-----------------|
|[只寫陣列::開始](#begin)|指向陣列中第一個元素的迭代器。|
|[寫唯一的Array::D](#data)|資料緩衝區的指標。|
|[只寫入陣列:結束](#end)|指向陣列中最後一個元素後加一的迭代器。|
|[只寫::快速通過](#fastpass)|表示陣列是否可以使用 FastPass 機制，這是由系統悄悄執行的最佳化作業。 請勿在您的程式碼中使用此屬性。|
|[只寫入陣列:長度](#length)|傳回陣列中的元素數目。|
|[只寫入陣列::設定](#set)|為指定的元素設定指定的值。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`WriteOnlyArray`

### <a name="requirements"></a>需求

編譯器選項: **/ZW**

**中繼資料:** 平臺.winmd

**命名空間：** Platform

## <a name="writeonlyarraybegin-method"></a><a name="begin"></a>只寫入陣列::開始方法

傳回陣列中第一個元素的指標。

### <a name="syntax"></a>語法

```cpp
T* begin() const;
```

### <a name="return-value"></a>傳回值

陣列中第一個元素的指標。

### <a name="remarks"></a>備註

這個迭代器可與 `std::sort` 這類 STL 演算法搭配使用，針對陣列元素執行作業。

## <a name="writeonlyarraydata-property"></a><a name="data"></a>寫唯一陣列::D

資料緩衝區的指標。

### <a name="syntax"></a>語法

```cpp
property T* Data{
   T* get() const;
}
```

### <a name="return-value"></a>傳回值

原始陣列位元組的指標。

## <a name="writeonlyarrayend-method"></a><a name="end"></a>只寫入陣列:結束方法

傳回陣列中最後一個元素後加一的指標。

### <a name="syntax"></a>語法

```cpp
T* end() const;
```

### <a name="return-value"></a>傳回值

陣列中最後一個元素後加一的指標迭代器。

### <a name="remarks"></a>備註

這個迭代器可與 STL 演算法搭配使用，針對陣列元素執行像是 `std::sort` 這類作業。

## <a name="writeonlyarrayfastpass-property"></a><a name="fastpass"></a>只寫入陣列::快速通道屬性

表示是否可以執行內部 FastPass 最佳化。 不適合由使用者程式碼所使用。

### <a name="syntax"></a>語法

```cpp
property bool FastPass{
   bool get() const;
}
```

### <a name="return-value"></a>傳回值

表示陣列是否為 FastPass 的布林值。

## <a name="writeonlyarrayget-method"></a><a name="get"></a>只寫入陣列::獲取方法

傳回位於指定之索引處的元素。

### <a name="syntax"></a>語法

```cpp
T& get(unsigned int indexArg) const;
```

### <a name="parameters"></a>參數

*指數阿格*<br/>
要使用的索引。

### <a name="return-value"></a>傳回值

## <a name="writeonlyarraylength-property"></a><a name="length"></a>只寫入陣列:長度屬性

傳回呼叫端配置之陣列中元素數目。

### <a name="syntax"></a>語法

```cpp
property unsigned int Length{
   unsigned int get() const;
}
```

### <a name="return-value"></a>傳回值

陣列中的項目數。

## <a name="writeonlyarrayset-function"></a><a name="set"></a>只寫入陣列::設定函數

在陣列中指定的索引處設定指定的值。

### <a name="syntax"></a>語法

```cpp
T& set(
   unsigned int indexArg,
   T valueArg);
```

### <a name="parameters"></a>參數

*指數阿格*<br/>
要設定之元素的索引。

*值阿格*<br/>
要在 `indexArg` 設定的值。

### <a name="return-value"></a>傳回值

剛才設定之元素的參考。

### <a name="remarks"></a>備註

有關如何解釋 HRESULT 值的詳細資訊,請參閱 COM[錯誤代碼的結構](/windows/win32/com/structure-of-com-error-codes)。

## <a name="see-also"></a>另請參閱

[平台命名空間](platform-namespace-c-cx.md)<br/>
[在 C++ 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
