---
title: HStringReference 類別
ms.date: 07/15/2019
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::Get
- corewrappers/Microsoft::WRL::Wrappers::GetRawBuffer
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator==
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HStringReference class
- Microsoft::WRL::Wrappers::HStringReference::CopyTo method
- Microsoft::WRL::Wrappers::HStringReference::Get method
- Microsoft::WRL::Wrappers::HStringReference::HStringReference, constructor
- Microsoft::WRL::Wrappers::HStringReference::operator= operator
- Microsoft::WRL::Wrappers::HStringReference::operator== operator
- Microsoft::WRL::Wrappers::HStringReference::operator!= operator
- Microsoft::WRL::Wrappers::HStringReference::operator< operator
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
ms.openlocfilehash: 871696f4a970b1ef9d1f5d36d2e17184b93c9e8b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212978"
---
# <a name="hstringreference-class"></a>HStringReference 類別

表示從現有字串建立的 HSTRING。

## <a name="syntax"></a>語法

```cpp
class HStringReference;
```

## <a name="remarks"></a>備註

在新的 HSTRING 中，支援緩衝區的存留期不受 Windows 執行階段管理。 呼叫端會在堆疊框架上配置來源字串，以避免堆積配置，並消除記憶體流失的風險。 此外，呼叫端必須確保在附加 HSTRING 的存留期間，來源字串維持不變。 如需詳細資訊，請參閱[WindowsCreateStringReference 函數](/windows/win32/api/winstring/nf-winstring-windowscreatestringreference)。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                    | 說明
------------------------------------------------------- | -----------------------------------------------------------
[HStringReference：： HStringReference](#hstringreference) | 初始化 `HStringReference` 類別的新執行個體。

### <a name="public-methods"></a>公用方法

成員                              | 說明
----------------------------------- | ------------------------------------------------------------------
[HStringReference::CopyTo](#copyto) | 將目前的 `HStringReference` 物件複製到 HSTRING 物件。
[HStringReference：： Get](#get)       | 抓取基礎 HSTRING 控制碼的值。
[HStringReference：： GetRawBuffer](#getrawbuffer) | 抓取基礎字串資料的指標。

### <a name="public-operators"></a>公用運算子

名稱                                                  | 說明
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference：： operator =](#operator-assign)       | 將另一個物件的值移 `HStringReference` 至目前的 `HStringReference` 物件。
[HStringReference：： operator = =](#operator-equality)    | 指出兩個參數是否相等。
[HStringReference：： operator！ =](#operator-inequality)  | 指出兩個參數是否不相等。
[HStringReference：： operator&lt;](#operator-less-than) | 指出第一個參數是否小於第二個參數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`HStringReference`

## <a name="requirements"></a>需求

**標頭：** corewrappers。h

**命名空間：** Microsoft：： WRL：：包裝函式

## <a name="hstringreferencecopyto"></a><a name="copyto"></a>HStringReference：： CopyTo

將目前的 `HStringReference` 物件複製到 HSTRING 物件。

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>參數

*字串*<br/>
接收復本的 HSTRING。

### <a name="remarks"></a>備註

這個方法會呼叫[WindowsDuplicateString](/windows/win32/api/winstring/nf-winstring-windowsduplicatestring)函數。

## <a name="hstringreferenceget"></a><a name="get"></a>HStringReference：： Get

抓取基礎 HSTRING 控制碼的值。

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>傳回值

基礎 HSTRING 控制碼的值。

## <a name="hstringreferencegetrawbuffer"></a><a name="getrawbuffer"></a>HStringReference：： GetRawBuffer

抓取基礎字串資料的指標。

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>參數

*長度***`int`** 接收資料長度之變數的指標。

### <a name="return-value"></a>傳回值

**`const`** 基礎字串資料的指標。

## <a name="hstringreferencehstringreference"></a><a name="hstringreference"></a>HStringReference：： HStringReference

初始化 `HStringReference` 類別的新執行個體。

```cpp
template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest]) throw();

template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest],
                 unsigned int len) throw();

HStringReference(HStringReference&& other) throw();
```

### <a name="parameters"></a>參數

*sizeDest*<br/>
範本參數，指定目的地緩衝區的大小 `HStringReference` 。

*字串*<br/>
寬字元字串的參考。

*len*<br/>
要在這項作業中使用的*str*參數緩衝區長度上限。 如果未指定*len*參數，則會使用整個*str*參數。 如果*len*大於*sizeDest*， *len*會設定為*sizeDest*-1。

*另一方面*<br/>
另一個 `HStringReference` 物件。

### <a name="remarks"></a>備註

第一個函式會初始化新的 `HStringReference` 物件，其大小與參數*str*相同。

第二個函式會初始化新的 `HStringReference` 物件，其大小會由參數*len*specifeid。

第三個函式會將新的 `HStringReference` 物件初始化為*另*一個參數的值，然後終結*另*一個參數。

## <a name="hstringreferenceoperator"></a><a name="operator-assign"></a>HStringReference：： operator =

將另一個物件的值移 `HStringReference` 至目前的 `HStringReference` 物件。

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>參數

*另一方面*<br/>
現有的 `HStringReference` 物件。

### <a name="remarks"></a>備註

現有*其他*物件的值會複製到目前的 `HStringReference` 物件，然後再終結*另*一個物件。

## <a name="hstringreferenceoperator"></a><a name="operator-equality"></a>HStringReference：： operator = =

指出兩個參數是否相等。

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較的第一個參數。 *lhs*可以是 `HStringReference` 物件或 HSTRING 控制碼。

*rhs*<br/>
要比較的第二個參數。  *rhs*可以是 `HStringReference` 物件或 HSTRING 控制碼。

### <a name="return-value"></a>傳回值

**`true`** 如果*lhs*和*rhs*參數相等，則為，否則為 **`false`** 。

## <a name="hstringreferenceoperator"></a><a name="operator-inequality"></a>HStringReference：： operator！ =

指出兩個參數是否不相等。

```cpp
inline bool operator!=(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較的第一個參數。 *lhs*可以是 `HStringReference` 物件或 HSTRING 控制碼。

*rhs*<br/>
要比較的第二個參數。  *rhs*可以是 `HStringReference` 物件或 HSTRING 控制碼。

### <a name="return-value"></a>傳回值

**`true`** 如果*lhs*和*rhs*參數不相等，則為，否則為 **`false`** 。

## <a name="hstringreferenceoperatorlt"></a><a name="operator-less-than"></a>HStringReference：： operator&lt;

指出第一個參數是否小於第二個參數。

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較的第一個參數。 *lhs*可以是的參考 `HStringReference` 。

*rhs*<br/>
要比較的第二個參數。  *rhs*可以是的參考 `HStringReference` 。

### <a name="return-value"></a>傳回值

**`true`** 如果*lhs*參數小於*rhs*參數，則為，否則為 **`false`** 。
