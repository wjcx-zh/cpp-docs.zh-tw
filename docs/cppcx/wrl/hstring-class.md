---
title: HString 類別
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
- corewrappers/Microsoft::WRL::Wrappers::HString::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HString::Detach
- corewrappers/Microsoft::WRL::Wrappers::HString::Get
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
ms.openlocfilehash: 19ef11a5d33e69bb77049e450df1b386528b7f7b
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784620"
---
# <a name="hstring-class"></a>HString 類別

協助程式類別來管理的存留期[HSTRING](/windows/desktop/WinRT/hstring)使用 RAII 模式。

## <a name="syntax"></a>語法

```cpp
class HString;
```

## <a name="remarks"></a>備註

Windows 執行階段會提供透過字串存取[HSTRING](/windows/desktop/WinRT/hstring)控制代碼。 `HString`類別提供方便函式和運算子，以簡化 HSTRING 控制代碼的使用。 這個類別可以處理您透過使用 RAII 模式，它擁有的 HSTRING 的存留期。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                | 描述
----------------------------------- | -----------------------------------------------------
[HString::HString](#hstring)        | 初始化 `HString` 類別的新執行個體。
[HString:: ~ HString](#tilde-hstring) | 終結的目前執行個體`HString`類別。

### <a name="public-methods"></a>公用方法

名稱                                     | 描述
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString::Attach](#attach)               | 將指定`HString`物件與目前`HString`物件。
[HString::CopyTo](#copyto)               | 複製目前`HString`到 HSTRING 物件的物件。
[HString::Detach](#detach)               | 解除指定`HString`與其基礎值的物件。
[HString::Get](#get)                     | 擷取基礎 HSTRING 控制代碼的值。
[HString::GetAddressOf](#getaddressof)   | 擷取基礎 HSTRING 控制代碼的指標。
[HString::IsValid](#isvalid)             | 指出是否目前`HString`物件是否有效。
[HString::MakeReference](#makereference) | 建立`HStringReference`從指定的字串參數的物件。
[HString::Release](#release)             | 會刪除基礎字串值，並初始化目前`HString`為空值的物件。
[HString::Set](#set)                     | 設定目前的值`HString`設為指定的寬字元字串的物件或`HString`參數。

### <a name="public-operators"></a>公用運算子

名稱                                         | 描述
-------------------------------------------- | ----------------------------------------------------------------------------
[HString::operator=](#operator-assign)       | 將另一個值移`HString`物件與目前`HString`物件。
[HString::operator==](#operator-equality)    | 指出兩個參數是否相等。
[HString::operator!=](#operator-inequality)  | 表示兩個參數是否不相等。
[HString::operator&lt;](#operator-less-than) | 指出第一個參數是否小於第二個參數。

## <a name="inheritance-hierarchy"></a>繼承階層

`HString`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="tilde-hstring"></a>HString:: ~ HString

終結的目前執行個體`HString`類別。

```cpp
~HString() throw()
```

## <a name="attach"></a>HString::Attach

將指定`HString`物件與目前`HString`物件。

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>參數

*hstr*<br/>
現有的 `HString` 物件。

## <a name="copyto"></a>HString::CopyTo

複製目前`HString`到 HSTRING 物件的物件。

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>參數

*str*<br/>
接收複本的 HSTRING。

### <a name="remarks"></a>備註

這個方法會呼叫[WindowsDuplicateString](/windows/desktop/api/winstring/nf-winstring-windowsduplicatestring)函式。

## <a name="detach"></a>HString::Detach

解除指定`HString`與其基礎值的物件。

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>傳回值

基礎`HString`卸離作業啟動之前的值。

## <a name="get"></a>HString::Get

擷取基礎 HSTRING 控制代碼的值。

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>傳回值

基礎 HSTRING 控制代碼的值

## <a name="getaddressof"></a>HString::GetAddressOf

擷取基礎 HSTRING 控制代碼的指標。

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>傳回值

基礎 HSTRING 控制代碼指標。

### <a name="remarks"></a>備註

此作業之後，就會終結基礎 HSTRING 控制代碼的字串值。

## <a name="hstring"></a>HString::HString

初始化 `HString` 類別的新執行個體。

```cpp
HString() throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>參數

*hstr*<br/>
HSTRING 控制代碼。

*other*<br/>
現有的 `HString` 物件。

### <a name="remarks"></a>備註

第一個建構函式初始化新`HString`是空的物件。

第二個建構函式初始化新`HString`的現有值的物件*其他*參數，然後終結*其他*參數。

## <a name="isvalid"></a>HString::IsValid

指出是否目前`HString`物件是否為空的。

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>參數

**真**如果目前`HString`物件不是空的否則**false**。

## <a name="makereference"></a>HString::MakeReference

建立`HStringReference`從指定的字串參數的物件。

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
樣板參數，指定大小的目的地`HStringReference`緩衝區。

*str*<br/>
寬字元字串的參考。

*len*<br/>
最大長度*str*来使用這項作業中的參數緩衝區。 如果*len*參數未指定，整個*str*參數使用。

### <a name="return-value"></a>傳回值

`HStringReference`物件，其值為與指定相同*str*參數。

## <a name="operator-assign"></a>Hstring:: Operator = 運算子

將另一個值移`HString`物件與目前`HString`物件。

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>參數

*other*<br/>
現有的 `HString` 物件。

### <a name="remarks"></a>備註

現有的值*其他*物件會複製到目前`HString`物件，然後*其他*物件被終結。

## <a name="operator-equality"></a>Hstring:: Operator = = 運算子

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
要比較的第一個參數。 *lhs*可以是`HString`或`HStringReference`物件或 HSTRING 控制代碼。

*rhs*<br/>
要比較的第二個參數。*rhs*可以是`HString`或`HStringReference`物件或 HSTRING 控制代碼。

### <a name="return-value"></a>傳回值

**真**如果*lhs*並*rhs*參數不相等，否則**false**。

## <a name="operator-inequality"></a>Hstring:: Operator ！ = 運算子

表示兩個參數是否不相等。

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
要比較的第一個參數。 *lhs*可以是`HString`或`HStringReference`物件或 HSTRING 控制代碼。

*rhs*<br/>
要比較的第二個參數。*rhs*可以是`HString`或`HStringReference`物件或 HSTRING 控制代碼。

### <a name="return-value"></a>傳回值

**真**如果*lhs*並*rhs*參數不相等，否則**false**。

## <a name="operator-less-than"></a>Hstring:: Operator&lt;運算子

指出第一個參數是否小於第二個參數。

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較的第一個參數。 *lhs*可以是參考`HString`。

*rhs*<br/>
要比較的第二個參數。 *rhs*可以是參考`HString`。

### <a name="return-value"></a>傳回值

**真**如果*lhs*參數是小於*rhs*參數，否則**false**。

## <a name="release"></a>HString::Release

會刪除基礎字串值，並初始化目前`HString`為空值的物件。

```cpp
void Release() throw()
```

## <a name="set"></a>HString::Set

設定目前的值`HString`設為指定的寬字元字串的物件或`HString`參數。

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
最大長度*str*指派給目前的參數`HString`物件。

*hstr*<br/>
現有的 `HString` 物件。
