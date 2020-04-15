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
ms.openlocfilehash: fd064f97081fad1a9df9de0865bb7c46ad5b4484
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371416"
---
# <a name="hstringreference-class"></a>HStringReference 類別

表示從現有字串建立的 HSTRING。

## <a name="syntax"></a>語法

```cpp
class HStringReference;
```

## <a name="remarks"></a>備註

新 HSTRING 中備份緩衝區的存留期不由 Windows 運行時管理。 調用方在堆疊幀上分配源字串,以避免堆分配並消除記憶體洩漏的風險。 此外,調用方必須確保原始字串在附加 HSTRING 的生存期內保持不變。 有關詳細資訊,請參閱[Windows 建立 String 參照函數](/windows/win32/api/winstring/nf-winstring-windowscreatestringreference)。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                    | 描述
------------------------------------------------------- | -----------------------------------------------------------
[HString 參考::HString 參考](#hstringreference) | 將 `HStringReference` 類別的新執行個體初始化。

### <a name="public-methods"></a>公用方法

member                              | 描述
----------------------------------- | ------------------------------------------------------------------
[HStringReference::CopyTo](#copyto) | 將當前`HStringReference`物件複製到 HSTRING 物件。
[HString 參考:取得](#get)       | 檢索基礎 HSTRING 句柄的值。
[HString 參考::獲取原始緩衝區](#getrawbuffer) | 檢索指向基礎字串數據的指標。

### <a name="public-operators"></a>公用運算子

名稱                                                  | 描述
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HString 參考::運算符*](#operator-assign)       | 將另一`HStringReference`個對象的值移動到`HStringReference`當前 物件。
[HString 參考::運算符 *](#operator-equality)    | 指示兩個參數是否相等。
[HString 參考::操作員!](#operator-inequality)  | 指示兩個參數是否不相等。
[HString 參考::運算子&lt;](#operator-less-than) | 指示第一個參數是否小於第二個參數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`HStringReference`

## <a name="requirements"></a>需求

**標題:** 核心包裝.h

**命名空間:** 微軟::WRL:包裝

## <a name="hstringreferencecopyto"></a><a name="copyto"></a>HString 參考::複製到

將當前`HStringReference`物件複製到 HSTRING 物件。

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

## <a name="hstringreferenceget"></a><a name="get"></a>HString 參考:取得

檢索基礎 HSTRING 句柄的值。

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>傳回值

基礎 HSTRING 句柄的值。

## <a name="hstringreferencegetrawbuffer"></a><a name="getrawbuffer"></a>HString 參考::獲取原始緩衝區

檢索指向基礎字串數據的指標。

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>參數

*長度*指向接收數據長度的**int**變數的指標。

### <a name="return-value"></a>傳回值

指向基礎字串資料的**const**指標。

## <a name="hstringreferencehstringreference"></a><a name="hstringreference"></a>HString 參考::HString 參考

將 `HStringReference` 類別的新執行個體初始化。

```cpp
template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest]) throw();

template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest],
                 unsigned int len) throw();

HStringReference(HStringReference&& other) throw();
```

### <a name="parameters"></a>參數

*大小 D 最大*<br/>
指定目標`HStringReference`緩衝區大小的範本參數。

*Str*<br/>
對寬字元字串的引用。

*萊恩*<br/>
要在此操作中使用*str*參數緩衝區的最大長度。 如果未指定*len*參數,則使用整個*str*參數。 如果*len*大於*大小 D,**則 len*設定為大小 D*最大*-1。

*其他*<br/>
另`HStringReference`一個物件。

### <a name="remarks"></a>備註

第一個建構函數初始化了與`HStringReference`參數*str*大小相同的新物件。

第二個建構函數初始化了大小`HStringReference`按參數*len*指定的新物件。

第三個建構函數將新`HStringReference`物件初始化到*其他*參數的值,然後銷毀*另一個*參數。

## <a name="hstringreferenceoperator"></a><a name="operator-assign"></a>HString 參考::運算符*

將另一`HStringReference`個對象的值移動到`HStringReference`當前 物件。

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>參數

*其他*<br/>
現有的 `HStringReference` 物件。

### <a name="remarks"></a>備註

現有*其他*物件的值將複製到`HStringReference`當前 物件,然後銷毀*其他*物件。

## <a name="hstringreferenceoperator"></a><a name="operator-equality"></a>HString 參考::運算符 *

指示兩個參數是否相等。

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
要比較的第一個參數。 *lhs*可以`HStringReference`是 物件或 HSTRING 句柄。

*rhs*<br/>
要比較的第二個參數。  *rhs*可以`HStringReference`是 物件或 HSTRING 句柄。

### <a name="return-value"></a>傳回值

如果*lhs*和*rhs*參數相等,**則為 true;** 否則,**假**。

## <a name="hstringreferenceoperator"></a><a name="operator-inequality"></a>HString 參考::操作員!

指示兩個參數是否不相等。

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
要比較的第一個參數。 *lhs*可以`HStringReference`是 物件或 HSTRING 句柄。

*rhs*<br/>
要比較的第二個參數。  *rhs*可以`HStringReference`是 物件或 HSTRING 句柄。

### <a name="return-value"></a>傳回值

如果*lhs*和*rhs*參數不相等,**則為 true;** 否則,**假**。

## <a name="hstringreferenceoperatorlt"></a><a name="operator-less-than"></a>HString 參考::運算子&lt;

指示第一個參數是否小於第二個參數。

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較的第一個參數。 *lhs*可以是`HStringReference`對 的引用。

*rhs*<br/>
要比較的第二個參數。  *rhs*可以是對`HStringReference`的引用。

### <a name="return-value"></a>傳回值

如果*lhs*參數小於*rhs*參數,**則為 true;** 否則,**假**。
