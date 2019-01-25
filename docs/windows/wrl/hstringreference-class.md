---
title: HStringReference 類別
ms.date: 09/25/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::Get
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
ms.openlocfilehash: b9d2e49d0a7e1321e2259c06e1313a90d55dc90e
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893245"
---
# <a name="hstringreference-class"></a>HStringReference 類別

表示從現有字串建立的 HSTRING。

## <a name="syntax"></a>語法

```cpp
class HStringReference;
```

## <a name="remarks"></a>備註

新的 HSTRING 中支援緩衝區的存留期不受 Windows 執行階段。 呼叫端配置來源字串上的堆疊框架，以避免堆積配置，並排除記憶體流失的風險。 此外，呼叫端必須確保來源字串附加的 HSTRING 的存留期間會保持不變。 如需詳細資訊，請參閱 < [WindowsCreateStringReference 函式](/windows/desktop/api/winstring/nf-winstring-windowscreatestringreference)。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                    | 描述
------------------------------------------------------- | -----------------------------------------------------------
[Hstringreference:: Hstringreference](#hstringreference) | 初始化 `HStringReference` 類別的新執行個體。

### <a name="public-methods"></a>公用方法

成員                              | 描述
----------------------------------- | ------------------------------------------------------------------
[HStringReference::CopyTo](#copyto) | 複製目前`HStringReference`到 HSTRING 物件的物件。
[HStringReference::Get](#get)       | 擷取基礎 HSTRING 控制代碼的值。

### <a name="public-operators"></a>公用運算子

名稱                                                  | 描述
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference::operator=](#operator-assign)       | 將另一個值移`HStringReference`物件與目前`HStringReference`物件。
[HStringReference::operator==](#operator-equality)    | 指出兩個參數是否相等。
[HStringReference::operator!=](#operator-inequality)  | 表示兩個參數是否不相等。
[HStringReference::operator&lt;](#operator-less-than) | 指出第一個參數是否小於第二個參數。

## <a name="inheritance-hierarchy"></a>繼承階層

`HStringReference`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="copyto"></a>HStringReference::CopyTo

複製目前`HStringReference`到 HSTRING 物件的物件。

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

## <a name="get"></a>HStringReference::Get

擷取基礎 HSTRING 控制代碼的值。

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>傳回值

基礎 HSTRING 控制代碼的值。

## <a name="hstringreference"></a>Hstringreference:: Hstringreference

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
樣板參數，指定大小的目的地`HStringReference`緩衝區。

*str*<br/>
寬字元字串的參考。

*len*<br/>
最大長度*str*来使用這項作業中的參數緩衝區。 如果*len*參數未指定，整個*str*參數使用。 如果*len*大於*sizeDest*， *len*設定為*sizeDest*-1。

*other*<br/>
另一個`HStringReference`物件。

### <a name="remarks"></a>備註

第一個建構函式初始化新`HStringReference`大小參數相同的物件*str*。

第二個建構函式初始化新`HStringReference`物件參數大小 specifeid *len*。

第三個建構函式初始化新`HStringReference`物件的值*其他*參數，然後終結*其他*參數。

## <a name="operator-assign"></a>HStringReference::operator=

將另一個值移`HStringReference`物件與目前`HStringReference`物件。

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>參數

*other*<br/>
現有的 `HStringReference` 物件。

### <a name="remarks"></a>備註

現有的值*其他*物件會複製到目前`HStringReference`物件，然後*其他*物件被終結。

## <a name="operator-equality"></a>Hstringreference:: Operator = =

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
要比較的第一個參數。 *lhs*可以是`HStringReference`物件或 HSTRING 控制代碼。

*rhs*<br/>
要比較的第二個參數。  *rhs*可以是`HStringReference`物件或 HSTRING 控制代碼。

### <a name="return-value"></a>傳回值

**真**如果*lhs*並*rhs*參數不相等，否則**false**。

## <a name="operator-inequality"></a>Hstringreference:: Operator ！ =

表示兩個參數是否不相等。

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
要比較的第一個參數。 *lhs*可以是`HStringReference`物件或 HSTRING 控制代碼。

*rhs*<br/>
要比較的第二個參數。  *rhs*可以是`HStringReference`物件或 HSTRING 控制代碼。

### <a name="return-value"></a>傳回值

**真**如果*lhs*並*rhs*參數不相等，否則**false**。

## <a name="operator-less-than"></a>HStringReference::operator&lt;

指出第一個參數是否小於第二個參數。

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較的第一個參數。 *lhs*可以是參考`HStringReference`。

*rhs*<br/>
要比較的第二個參數。  *rhs*可以是參考`HStringReference`。

### <a name="return-value"></a>傳回值

**真**如果*lhs*參數是小於*rhs*參數，否則**false**。
