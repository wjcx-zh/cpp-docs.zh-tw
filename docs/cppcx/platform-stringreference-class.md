---
title: Platform::StringReference 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::StringReference::StringReference
- VCCORLIB/Platform::StringReference::Data
- VCCORLIB/Platform::StringReference::Length
- VCCORLIB/Platform::StringReference::GetHSTRING
- VCCORLIB/Platform::StringReference::GetString
ms.assetid: 2d09c7ec-0f16-458e-83ed-7225a1b9221e
ms.openlocfilehash: 4748eecdf67ae5a60ddf97783a934a05e80b406c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374654"
---
# <a name="platformstringreference-class"></a>Platform::StringReference 類別

可以用來從 `Platform::String^` 輸入參數將字串資料傳遞給其他方法的最佳化類型，可將複製作業減至最少。

## <a name="syntax"></a>語法

```cpp
class StringReference
```

### <a name="remarks"></a>備註

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[字串引用::字串引用](#ctor)|用來建立 `StringReference`執行個體的兩個建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[字串參考::D](#data)|傳回字串資料當做 char16 值的陣列。|
|[字串參考:長度](#length)|傳回字串中的字元數。|
|[字串參考::獲取HSTRING](#gethstring)|傳回字串資料當做 HSTRING。|
|[字串引用::取得String](#getstring)|傳回字串資料當做 `Platform::String^`。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[字串參考::運算元*](#operator-assign)|將 `StringReference` 指定給新的 `StringReference` 執行個體。|
|[字串引用::運算子()](#operator-call)|將 `StringReference` 轉換成 `Platform::String^`。|

### <a name="requirements"></a>需求

**受支援的最小用戶端:** 視窗 8

**受支援的伺服器最少:** 視窗伺服器 2012

**命名空間：** Platform

**標頭：** vccorlib.h

## <a name="stringreferencedata-method"></a><a name="data"></a>字串參考::Data 方法

傳回這個 `StringReference` 的內容作為 char16 值的陣列。

### <a name="syntax"></a>語法

```cpp
const ::default::char16 * Data() const;
```

### <a name="return-value"></a>傳回值

char16 UNICODE 文字字元陣列。

## <a name="stringreferencegethstring-method"></a><a name="gethstring"></a>字串引用:getHSTRING 方法

傳回 `__abi_HSTRING` 形式的字串內容。

### <a name="syntax"></a>語法

```cpp
__abi_HSTRING GetHSTRING() const;
```

### <a name="return-value"></a>傳回值

包含字串資料的 `__abi_HSTRING`。

### <a name="remarks"></a>備註

## <a name="stringreferencegetstring-method"></a><a name="getstring"></a>字串引用::取得字串方法

傳回 `Platform::String^` 形式的字串內容。

### <a name="syntax"></a>語法

```cpp
__declspec(no_release_return) __declspec(no_refcount)
    ::Platform::String^ GetString() const;
```

### <a name="return-value"></a>傳回值

包含字串資料的 `Platform::String^`。

## <a name="stringreferencelength-method"></a><a name="length"></a>字串引用:長度方法

傳回字串中的字元數。

### <a name="syntax"></a>語法

```cpp
unsigned int Length() const;
```

### <a name="return-value"></a>傳回值

指定字串中之字元數的不帶正負號的整數。

### <a name="remarks"></a>備註

## <a name="stringreferenceoperator-operator"></a><a name="operator-assign"></a>字串參考:::運算元= 運算子

將指定的物件指定給目前的 `StringReference` 物件。

### <a name="syntax"></a>語法

```cpp
StringReference& operator=(const StringReference& __fstrArg);
StringReference& operator=(const ::default::char16* __strArg);
```

### <a name="parameters"></a>參數

*__fstrArg*<br/>
用來初始化目前 `StringReference` 物件之 `StringReference` 物件的位址。

*__strArg*<br/>
用來初始化目前 `StringReference` 物件之 char16 值陣列的指標。

### <a name="return-value"></a>傳回值

類型為 `StringReference` 之物件的參考。

### <a name="remarks"></a>備註

因為它是`StringReference`標準C++類,而不是 ref 類,所以它不出現在**對象瀏覽器**中。

## <a name="stringreferenceoperator--operator"></a><a name="operator-call"></a>字串參考::運算子() 運算子

將 `StringReference` 物件轉換成 `Platform::String^` 物件。

### <a name="syntax"></a>語法

```cpp
__declspec(no_release_return) __declspec(no_refcount)
         operator ::Platform::String^() const;
```

### <a name="return-value"></a>傳回值

`Platform::String` 類型之物件的控制代碼。

## <a name="stringreferencestringreference-constructor"></a><a name="ctor"></a>字串引用::字串引用建構函式

將 `StringReference` 類別的新執行個體初始化。

### <a name="syntax"></a>語法

```cpp
StringReference();
StringReference(const StringReference& __fstrArg);
StringReference(const ::default::char16* __strArg);
StringReference(const ::default::char16* __strArg, size_t __lenArg);
```

### <a name="parameters"></a>參數

*__fstrArg*<br/>
其資料用來初始化新執行個體的 `StringReference`。

*__strArg*<br/>
用來初始化新執行個體之 char16 值陣列的指標。

*__lenArg*<br/>
`__strArg` 中的元素數目。

### <a name="remarks"></a>備註

此建構函式的第一個版本是預設建構函式。 第二個版本會從 `StringReference` 參數指定的物件初始化新的 `__fstrArg` 執行個體類別。 第三和第四個多載會從 char16 值的陣列初始化新的 `StringReference` 執行個體。 char16 表示 16 位元的 UNICODE 文字字元。

## <a name="see-also"></a>另請參閱

[Platform::StringReference 類別](../cppcx/platform-stringreference-class.md)
