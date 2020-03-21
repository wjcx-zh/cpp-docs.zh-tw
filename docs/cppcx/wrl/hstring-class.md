---
title: HString 類別
ms.date: 07/15/2019
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
- corewrappers/Microsoft::WRL::Wrappers::HString::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HString::Detach
- corewrappers/Microsoft::WRL::Wrappers::HString::Get
- corewrappers/Microsoft::WRL::Wrappers::HString::GetRawBuffer
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator==
- corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
- corewrappers/Microsoft::WRL::Wrappers::HString::Release
- corewrappers/Microsoft::WRL::Wrappers::HString::Set
- corewrappers/Microsoft::WRL::Wrappers::HString::~HString
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HString class
- Microsoft::WRL::Wrappers::HString::Attach method
- Microsoft::WRL::Wrappers::HString::CopyTo method
- Microsoft::WRL::Wrappers::HString::Detach method
- Microsoft::WRL::Wrappers::HString::Get method
- Microsoft::WRL::Wrappers::HString::GetAddressOf method
- Microsoft::WRL::Wrappers::HString::HString, constructor
- Microsoft::WRL::Wrappers::HString::IsValid method
- Microsoft::WRL::Wrappers::HString::MakeReference method
- Microsoft::WRL::Wrappers::HString::operator= operator
- Microsoft::WRL::Wrappers::HString::operator== operator
- Microsoft::WRL::Wrappers::HString::operator!= operator
- Microsoft::WRL::Wrappers::HString::operator< operator
- Microsoft::WRL::Wrappers::HString::Release method
- Microsoft::WRL::Wrappers::HString::Set method
- Microsoft::WRL::Wrappers::HString::~HString, destructor
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
ms.openlocfilehash: 38979a058cd6a8b029961708b4197daea2826d85
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077176"
---
# <a name="hstring-class"></a>HString 類別

協助程式類別，用來管理使用 RAII 模式之[HSTRING](/windows/win32/WinRT/hstring)的存留期。

## <a name="syntax"></a>語法

```cpp
class HString;
```

## <a name="remarks"></a>備註

Windows 執行階段透過[HSTRING](/windows/win32/WinRT/hstring)控制碼提供字串的存取權。 `HString` 類別提供便利的函式和運算子，以簡化使用 HSTRING 控制碼的工作。 這個類別可以透過 RAII 模式來處理其所擁有之 HSTRING 的存留期。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                | 描述
----------------------------------- | -----------------------------------------------------
[HString：： HString](#hstring)        | 將 `HString` 類別的新執行個體初始化。
[HString：： ~ HString](#tilde-hstring) | 終結 `HString` 類別的目前實例。

### <a name="public-methods"></a>公用方法

名稱                                     | 描述
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString：： Attach](#attach)               | 將指定的 `HString` 物件與目前的 `HString` 物件產生關聯。
[HString：： CopyTo](#copyto)               | 將目前的 `HString` 物件複製到 HSTRING 物件。
[HString：:D etach](#detach)               | 解除指定的 `HString` 物件與其基礎值的對應。
[HString：： Get](#get)                     | 抓取基礎 HSTRING 控制碼的值。
[HString：： GetAddressOf](#getaddressof)   | 抓取基礎 HSTRING 控制碼的指標。
[HString：： GetRawBuffer](#getrawbuffer)   | 抓取基礎字串資料的指標。
[HString：： IsValid](#isvalid)             | 指出目前的 `HString` 物件是否有效。
[HString：： MakeReference](#makereference) | 從指定的字串參數建立 `HStringReference` 物件。
[HString：： Release](#release)             | 刪除基礎字串值，並將目前的 `HString` 物件初始化為空值。
[HString：： Set](#set)                     | 將目前 `HString` 物件的值設定為指定的寬字元字串或 `HString` 參數。

### <a name="public-operators"></a>公用運算子

名稱                                         | 描述
-------------------------------------------- | ----------------------------------------------------------------------------
[HString：： operator =](#operator-assign)       | 將另一個 `HString` 物件的值移至目前的 `HString` 物件。
[HString：： operator = =](#operator-equality)    | 指出兩個參數是否相等。
[HString：： operator！ =](#operator-inequality)  | 指出兩個參數是否不相等。
[HString：： operator&lt;](#operator-less-than) | 指出第一個參數是否小於第二個參數。

## <a name="inheritance-hierarchy"></a>繼承階層

`HString`

## <a name="requirements"></a>需求

**標頭：** corewrappers。h

**命名空間：** Microsoft：： WRL：：包裝函式

## <a name="hstringhstring"></a><a name="tilde-hstring"></a>HString：： ~ HString

終結 `HString` 類別的目前實例。

```cpp
~HString() throw()
```

## <a name="hstringattach"></a><a name="attach"></a>HString：： Attach

將指定的 `HString` 物件與目前的 `HString` 物件產生關聯。

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>參數

*hstr*<br/>
現有的 `HString` 物件。

## <a name="hstringcopyto"></a><a name="copyto"></a>HString：： CopyTo

將目前的 `HString` 物件複製到 HSTRING 物件。

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>參數

*str*<br/>
接收復本的 HSTRING。

### <a name="remarks"></a>備註

這個方法會呼叫[WindowsDuplicateString](/windows/win32/api/winstring/nf-winstring-windowsduplicatestring)函數。

## <a name="hstringdetach"></a><a name="detach"></a>HString：:D etach

解除指定的 `HString` 物件與其基礎值的對應。

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>傳回值

卸離作業開始之前的基礎 `HString` 值。

## <a name="hstringget"></a><a name="get"></a>HString：： Get

抓取基礎 HSTRING 控制碼的值。

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>傳回值

基礎 HSTRING 控制碼的值。

## <a name="hstringgetaddressof"></a><a name="getaddressof"></a>HString：： GetAddressOf

抓取基礎 HSTRING 控制碼的指標。

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>傳回值

基礎 HSTRING 控制碼的指標。

### <a name="remarks"></a>備註

在這項作業之後，會終結基礎 HSTRING 控制碼的字串值。

## <a name="hstringgetrawbuffer"></a><a name="getrawbuffer"></a>HString：： GetRawBuffer

抓取基礎字串資料的指標。

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>參數

*長度*接收資料長度之**int**變數的指標。

### <a name="return-value"></a>傳回值

基礎字串資料的**常數**指標。

## <a name="hstringhstring"></a><a name="hstring"></a>HString：： HString

將 `HString` 類別的新執行個體初始化。

```cpp
HString() throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>參數

*hstr*<br/>
HSTRING 控制碼。

*other*<br/>
現有的 `HString` 物件。

### <a name="remarks"></a>備註

第一個函式會初始化空白的新 `HString` 物件。

第二個函式會將新的 `HString` 物件初始化為現有*其他*參數的值，然後再終結*另*一個參數。

## <a name="hstringisvalid"></a><a name="isvalid"></a>HString：： IsValid

指出目前的 `HString` 物件是否為空白。

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>參數

如果目前 `HString` 物件不是空的，則為**true** ;否則**為 false**。

## <a name="hstringmakereference"></a><a name="makereference"></a>HString：： MakeReference

從指定的字串參數建立 `HStringReference` 物件。

```cpp
template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[ sizeDest]);

    template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[sizeDest],
              unsigned int len);
```

### <a name="parameters"></a>參數

*sizeDest*<br/>
範本參數，指定目的地 `HStringReference` 緩衝區的大小。

*str*<br/>
寬字元字串的參考。

*len*<br/>
要在這項作業中使用的*str*參數緩衝區長度上限。 如果未指定*len*參數，則會使用整個*str*參數。

### <a name="return-value"></a>傳回值

`HStringReference` 物件，其值與指定的*str*參數相同。

## <a name="hstringoperator-operator"></a><a name="operator-assign"></a>HString：： operator = 運算子

將另一個 `HString` 物件的值移至目前的 `HString` 物件。

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>參數

*other*<br/>
現有的 `HString` 物件。

### <a name="remarks"></a>備註

現有*其他*物件的值會複製到目前的 `HString` 物件，然後再終結*另*一個物件。

## <a name="hstringoperator-operator"></a><a name="operator-equality"></a>HString：： operator = = 運算子

指出兩個參數是否相等。

```cpp
inline bool operator==(
               const HString& lhs,
               const HString& rhs) throw()

inline bool operator==(
                const HString& lhs,
                const HStringReference& rhs) throw()

inline bool operator==(
                const HStringReference& lhs,
                const HString& rhs) throw()

inline bool operator==(
                 const HSTRING& lhs,
                 const HString& rhs) throw()

inline bool operator==(
                 const HString& lhs,
                 const HSTRING& rhs) throw()
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較的第一個參數。 *lhs*可以是 `HString` 或 `HStringReference` 物件，或是 HSTRING 控制碼。

*rhs*<br/>
要比較的第二個參數。*rhs*可以是 `HString` 或 `HStringReference` 物件，或是 HSTRING 控制碼。

### <a name="return-value"></a>傳回值

如果*lhs*和*rhs*參數相等，則為**true** ;否則**為 false**。

## <a name="hstringoperator-operator"></a><a name="operator-inequality"></a>HString：： operator！ = 運算子

指出兩個參數是否不相等。

```cpp
inline bool operator!=( const HString& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HStringReference& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HStringReference& rhs) throw()

inline bool operator!=( const HSTRING& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HSTRING& rhs) throw()
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較的第一個參數。 *lhs*可以是 `HString` 或 `HStringReference` 物件，或是 HSTRING 控制碼。

*rhs*<br/>
要比較的第二個參數。*rhs*可以是 `HString` 或 `HStringReference` 物件，或是 HSTRING 控制碼。

### <a name="return-value"></a>傳回值

如果*lhs*和*rhs*參數不相等，則為**true** ;否則**為 false**。

## <a name="hstringoperatorlt-operator"></a><a name="operator-less-than"></a>HString：： operator&lt; 運算子

指出第一個參數是否小於第二個參數。

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較的第一個參數。 *lhs*可以是 `HString`的參考。

*rhs*<br/>
要比較的第二個參數。 *rhs*可以是 `HString`的參考。

### <a name="return-value"></a>傳回值

如果*lhs*參數小於*rhs*參數，則為**true** ;否則**為 false**。

## <a name="hstringrelease"></a><a name="release"></a>HString：： Release

刪除基礎字串值，並將目前的 `HString` 物件初始化為空值。

```cpp
void Release() throw()
```

## <a name="hstringset"></a><a name="set"></a>HString：： Set

將目前 `HString` 物件的值設定為指定的寬字元字串或 `HString` 參數。

```cpp
HRESULT Set(
          const wchar_t* str) throw();
HRESULT Set(
          const wchar_t* str,
          unsigned int len
           ) throw();
HRESULT Set(
          const HSTRING& hstr
           ) throw();
```

### <a name="parameters"></a>參數

*str*<br/>
寬字元字串。

*len*<br/>
指派給目前 `HString` 物件的*str*參數長度上限。

*hstr*<br/>
現有的 `HString` 物件。
