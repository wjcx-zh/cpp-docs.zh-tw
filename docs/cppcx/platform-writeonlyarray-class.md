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
ms.openlocfilehash: 5652123d4866262515f804dba790af51610eb426
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500513"
---
# <a name="platformwriteonlyarray-class"></a>Platform::WriteOnlyArray 類別

表示一維陣列。當呼叫端傳遞陣列讓方法填滿其中元素時，就會將這個陣列當做輸入參數來傳遞。

這個 ref 類別在 vccorlib.h 中是宣告為私用，因此不會在中繼資料內發出，而且只能從 C++ 使用。 這個類別只做為用來接收呼叫端所配置之陣列的輸入參數。 您無法從使用者程式碼建構這個類別。 它可以讓 C++ 方法直接在陣列中寫入資料，這就稱為「 *FillArray* 」模式。 如需詳細資訊, 請參閱[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。

## <a name="syntax"></a>語法

```cpp
private ref class WriteOnlyArray<T, 1>
```

### <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

這些方法的存取範圍都是 internal，也就是說，您只能在 C++ 應用程式或元件內存取這些方法。

|名稱|說明|
|----------|-----------------|
|[WriteOnlyArray:: begin](#begin)|指向陣列中第一個元素的迭代器。|
|[WriteOnlyArray::Data](#data)|資料緩衝區的指標。|
|[WriteOnlyArray:: end](#end)|指向陣列中最後一個元素後加一的迭代器。|
|[WriteOnlyArray::FastPass](#fastpass)|表示陣列是否可以使用 FastPass 機制，這是由系統悄悄執行的最佳化作業。 請勿在您的程式碼中使用此屬性。|
|[WriteOnlyArray::Length](#length)|傳回陣列中的元素數目。|
|[WriteOnlyArray::set](#set)|為指定的元素設定指定的值。|

## <a name="inheritance-hierarchy"></a>繼承階層

`WriteOnlyArray`

### <a name="requirements"></a>需求

編譯器選項： **/ZW**

**中繼資料**Platform.winmd

**命名空間：** 平台

## <a name="begin"></a>  WriteOnlyArray::begin 方法

傳回陣列中第一個元素的指標。

### <a name="syntax"></a>語法

```cpp
T* begin() const;
```

### <a name="return-value"></a>傳回值

陣列中第一個元素的指標。

### <a name="remarks"></a>備註

這個迭代器可與 `std::sort` 這類 STL 演算法搭配使用，針對陣列元素執行作業。

## <a name="data"></a>  WriteOnlyArray::Data 屬性

資料緩衝區的指標。

### <a name="syntax"></a>語法

```cpp
property T* Data{
   T* get() const;
}
```

### <a name="return-value"></a>傳回值

原始陣列位元組的指標。

## <a name="end"></a>  WriteOnlyArray::end 方法

傳回陣列中最後一個元素後加一的指標。

### <a name="syntax"></a>語法

```cpp
T* end() const;
```

### <a name="return-value"></a>傳回值

陣列中最後一個元素後加一的指標迭代器。

### <a name="remarks"></a>備註

這個迭代器可與 STL 演算法搭配使用，針對陣列元素執行像是 `std::sort` 這類作業。

## <a name="fastpass"></a>  WriteOnlyArray::FastPass 屬性

表示是否可以執行內部 FastPass 最佳化。 不適合由使用者程式碼所使用。

### <a name="syntax"></a>語法

```cpp
property bool FastPass{
   bool get() const;
}
```

### <a name="return-value"></a>傳回值

表示陣列是否為 FastPass 的布林值。

## <a name="get"></a>WriteOnlyArray:: get 方法

傳回位於指定之索引處的元素。

### <a name="syntax"></a>語法

```cpp
T& get(unsigned int indexArg) const;
```

### <a name="parameters"></a>參數

*indexArg*<br/>
要使用的索引。

### <a name="return-value"></a>傳回值

## <a name="length"></a>  WriteOnlyArray::Length 屬性

傳回呼叫端配置之陣列中元素數目。

### <a name="syntax"></a>語法

```cpp
property unsigned int Length{
   unsigned int get() const;
}
```

### <a name="return-value"></a>傳回值

陣列中的項目數。

## <a name="set"></a>  WriteOnlyArray::set 函式

在陣列中指定的索引處設定指定的值。

### <a name="syntax"></a>語法

```cpp
T& set(
   unsigned int indexArg,
   T valueArg);
```

### <a name="parameters"></a>參數

*indexArg*<br/>
要設定之元素的索引。

*valueArg*<br/>
要在 `indexArg` 設定的值。

### <a name="return-value"></a>傳回值

剛才設定之元素的參考。

### <a name="remarks"></a>備註

如需如何解讀 HRESULT 值的詳細資訊, 請參閱[COM 錯誤碼的結構](/windows/win32/com/structure-of-com-error-codes)。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](platform-namespace-c-cx.md)<br/>
[在 C++ 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
