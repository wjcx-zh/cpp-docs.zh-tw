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
ms.openlocfilehash: 625d7b7d6fc001a6fb63144807b5f29d3620485b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371436"
---
# <a name="hstring-class"></a>HString 類別

使用 RAII 模式管理[HSTRING](/windows/win32/WinRT/hstring)的存留期的幫助器類。

## <a name="syntax"></a>語法

```cpp
class HString;
```

## <a name="remarks"></a>備註

Windows 運行時透過[HSTRING](/windows/win32/WinRT/hstring)句柄提供對字串的訪問。 該`HString`類提供方便的功能和運算符,以簡化使用 HSTRING 句柄。 此類可以通過 RAII 模式處理它擁有的 HSTRING 的存留期。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                | 描述
----------------------------------- | -----------------------------------------------------
[HString::HString](#hstring)        | 將 `HString` 類別的新執行個體初始化。
[HString::*HString](#tilde-hstring) | 銷毀`HString`類的當前實例。

### <a name="public-methods"></a>公用方法

名稱                                     | 描述
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString::附加](#attach)               | 將指定的`HString`物件與`HString`當前 物件關聯。
[HString::CopyTo](#copyto)               | 將當前`HString`物件複製到 HSTRING 物件。
[赫斯特林::D塔奇](#detach)               | 取消指定`HString`物件與其基礎值的關聯。
[HString:取得](#get)                     | 檢索基礎 HSTRING 句柄的值。
[HString:抓取位址](#getaddressof)   | 檢索指向基礎 HSTRING 句柄的指標。
[HString::取得原始緩衝區](#getrawbuffer)   | 檢索指向基礎字串數據的指標。
[HString::有效](#isvalid)             | 指示當前`HString`物件是否有效。
[HString::使參考](#makereference) | 從指定的`HStringReference`字串參數創建物件。
[HString::發佈](#release)             | 刪除基礎字串值並將當前`HString`物件歸為空值。
[HString::設定](#set)                     | 將目前的`HString`物件值設定到指定的寬字元字串或`HString`參數。

### <a name="public-operators"></a>公用運算子

名稱                                         | 描述
-------------------------------------------- | ----------------------------------------------------------------------------
[HString::運算符*](#operator-assign)       | 將另一`HString`個對象的值移動到`HString`當前 物件。
[HString::運算符*](#operator-equality)    | 指示兩個參數是否相等。
[HString::操作員!](#operator-inequality)  | 指示兩個參數是否不相等。
[HString::運算子&lt;](#operator-less-than) | 指示第一個參數是否小於第二個參數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`HString`

## <a name="requirements"></a>需求

**標題:** 核心包裝.h

**命名空間:** 微軟::WRL:包裝

## <a name="hstringhstring"></a><a name="tilde-hstring"></a>HString::*HString

銷毀`HString`類的當前實例。

```cpp
~HString() throw()
```

## <a name="hstringattach"></a><a name="attach"></a>HString::附加

將指定的`HString`物件與`HString`當前 物件關聯。

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>參數

*赫斯特*<br/>
現有的 `HString` 物件。

## <a name="hstringcopyto"></a><a name="copyto"></a>HString::複製到

將當前`HString`物件複製到 HSTRING 物件。

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>參數

*Str*<br/>
接收副本的 HSTRING。

### <a name="remarks"></a>備註

此方法呼叫[Windows 複製字串](/windows/win32/api/winstring/nf-winstring-windowsduplicatestring)函數。

## <a name="hstringdetach"></a><a name="detach"></a>赫斯特林::D塔奇

取消指定`HString`物件與其基礎值的關聯。

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>傳回值

分離操作`HString`開始之前的基礎值。

## <a name="hstringget"></a><a name="get"></a>HString:取得

檢索基礎 HSTRING 句柄的值。

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>傳回值

基礎 HSTRING 句柄的值

## <a name="hstringgetaddressof"></a><a name="getaddressof"></a>HString:抓取位址

檢索指向基礎 HSTRING 句柄的指標。

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>傳回值

指向基礎 HSTRING 句柄的指標。

### <a name="remarks"></a>備註

此操作後,將銷毀基礎 HSTRING 句柄的字串值。

## <a name="hstringgetrawbuffer"></a><a name="getrawbuffer"></a>HString::取得原始緩衝區

檢索指向基礎字串數據的指標。

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>參數

*長度*指向接收數據長度的**int**變數的指標。

### <a name="return-value"></a>傳回值

指向基礎字串資料的**const**指標。

## <a name="hstringhstring"></a><a name="hstring"></a>HString::HString

將 `HString` 類別的新執行個體初始化。

```cpp
HString() throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>參數

*赫斯特*<br/>
HSTRING 句柄。

*其他*<br/>
現有的 `HString` 物件。

### <a name="remarks"></a>備註

第一個構造函數初始化為空`HString`的新物件。

第二個建構函數將新`HString`物件初始化到現有*其他*參數的值,然後銷毀*其他*參數。

## <a name="hstringisvalid"></a><a name="isvalid"></a>HString::有效

指示當前`HString`物件是否為空。

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>參數

如果當前`HString`物件不為空,**則為 true;** 否則,**假**。

## <a name="hstringmakereference"></a><a name="makereference"></a>HString::使參考

從指定的`HStringReference`字串參數創建物件。

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

*大小 D 最大*<br/>
指定目標`HStringReference`緩衝區大小的範本參數。

*Str*<br/>
對寬字元字串的引用。

*萊恩*<br/>
要在此操作中使用*str*參數緩衝區的最大長度。 如果未指定*len*參數,則使用整個*str*參數。

### <a name="return-value"></a>傳回值

其`HStringReference`值與指定的*str*參數相同的物件。

## <a name="hstringoperator-operator"></a><a name="operator-assign"></a>HString:::運算符= 運算子

將另一`HString`個對象的值移動到`HString`當前 物件。

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>參數

*其他*<br/>
現有的 `HString` 物件。

### <a name="remarks"></a>備註

現有*其他*物件的值將複製到`HString`當前 物件,然後銷毀*其他*物件。

## <a name="hstringoperator-operator"></a><a name="operator-equality"></a>HString::::運算符=運算符

指示兩個參數是否相等。

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
要比較的第一個參數。 *lhs*可以`HString`是`HStringReference`物件或 物件,也可以是 HSTRING 句柄。

*rhs*<br/>
要比較的第二個參數。*rh 可以是*或`HString``HStringReference`物件,也可以是 HSTRING 句柄。

### <a name="return-value"></a>傳回值

如果*lhs*和*rhs*參數相等,**則為 true;** 否則,**假**。

## <a name="hstringoperator-operator"></a><a name="operator-inequality"></a>HString::操作員!= 操作員

指示兩個參數是否不相等。

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
要比較的第一個參數。 *lhs*可以`HString`是`HStringReference`物件或 物件,也可以是 HSTRING 句柄。

*rhs*<br/>
要比較的第二個參數。*rh 可以是*或`HString``HStringReference`物件,也可以是 HSTRING 句柄。

### <a name="return-value"></a>傳回值

如果*lhs*和*rhs*參數不相等,**則為 true;** 否則,**假**。

## <a name="hstringoperatorlt-operator"></a><a name="operator-less-than"></a>HString::操作員&lt;

指示第一個參數是否小於第二個參數。

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較的第一個參數。 *lhs*可以是`HString`對 的引用。

*rhs*<br/>
要比較的第二個參數。 *rhs*可以是對`HString`的引用。

### <a name="return-value"></a>傳回值

如果*lhs*參數小於*rhs*參數,**則為 true;** 否則,**假**。

## <a name="hstringrelease"></a><a name="release"></a>HString::發佈

刪除基礎字串值並將當前`HString`物件歸為空值。

```cpp
void Release() throw()
```

## <a name="hstringset"></a><a name="set"></a>HString::設定

將目前的`HString`物件值設定到指定的寬字元字串或`HString`參數。

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

*Str*<br/>
寬字元字串。

*萊恩*<br/>
分配給當前`HString`物件的*str*參數的最大長度。

*赫斯特*<br/>
現有的 `HString` 物件。
