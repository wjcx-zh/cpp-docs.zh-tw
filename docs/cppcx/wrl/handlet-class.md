---
title: HandleT 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Attach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Get
- corewrappers/Microsoft::WRL::Wrappers::HandleT::handle_
- corewrappers/Microsoft::WRL::Wrappers::HandleT::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
- corewrappers/Microsoft::WRL::Wrappers::HandleT::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
- corewrappers/Microsoft::WRL::Wrappers::HandleT::~HandleT
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleT class
- Microsoft::WRL::Wrappers::HandleT::Attach method
- Microsoft::WRL::Wrappers::HandleT::Close method
- Microsoft::WRL::Wrappers::HandleT::Detach method
- Microsoft::WRL::Wrappers::HandleT::Get method
- Microsoft::WRL::Wrappers::HandleT::handle_ data member
- Microsoft::WRL::Wrappers::HandleT::HandleT, constructor
- Microsoft::WRL::Wrappers::HandleT::InternalClose method
- Microsoft::WRL::Wrappers::HandleT::IsValid method
- Microsoft::WRL::Wrappers::HandleT::operator= operator
- Microsoft::WRL::Wrappers::HandleT::~HandleT, destructor
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
ms.openlocfilehash: 661d3cb92b20fc929a9bae3cad7bb55740e5e096
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213004"
---
# <a name="handlet-class"></a>HandleT 類別

表示物件的控制碼。

## <a name="syntax"></a>語法

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>參數

*HandleTraits*<br/>
定義控制碼之一般特性的[HandleTraits](handletraits-structure.md)結構實例。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱     | 說明
-------- | -----------------------------
`Traits` | `HandleTraits` 的同義字。

### <a name="public-constructors"></a>公用建構函式

名稱                                | 說明
----------------------------------- | --------------------------------------------------
[HandleT：： HandleT](#handlet)        | 初始化 `HandleT` 類別的新執行個體。
[HandleT：： ~ HandleT](#tilde-handlet) | 將類別的實例 `HandleT` 。

### <a name="public-methods"></a>公用方法

名稱                         | 說明
---------------------------- | ----------------------------------------------------------------------
[HandleT：： Attach](#attach)   | 將指定的控制碼與目前的物件產生關聯 `HandleT` 。
[HandleT：： Close](#close)     | 關閉目前的 `HandleT` 物件。
[HandleT：:D etach](#detach)   | 解除目前 `HandleT` 物件與其基礎控制碼的的對應。
[HandleT：： Get](#get)         | 取得基礎控制碼的值。
[HandleT：： IsValid](#isvalid) | 指出目前的 `HandleT` 物件是否代表控制碼。

### <a name="protected-methods"></a>保護方法

名稱                                     | 說明
---------------------------------------- | ------------------------------------
[HandleT：： InternalClose](#internalclose) | 關閉目前的 `HandleT` 物件。

### <a name="public-operators"></a>公用運算子

名稱                                   | 說明
-------------------------------------- | ----------------------------------------------------------------------------------
[HandleT：： operator =](#operator-assign) | 將指定之物件的值移 `HandleT` 至目前的 `HandleT` 物件。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                        | 說明
--------------------------- | ----------------------------------------------------------------
[HandleT：： handle_](#handle) | 包含物件所代表的控制碼 `HandleT` 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`HandleT`

## <a name="requirements"></a>需求

**標頭：** corewrappers。h

**命名空間：** Microsoft：： WRL：：包裝函式

## <a name="handlethandlet"></a><a name="tilde-handlet"></a>HandleT：： ~ HandleT

將類別的實例 `HandleT` 。

```cpp
~HandleT();
```

## <a name="handletattach"></a><a name="attach"></a>HandleT：： Attach

將指定的控制碼與目前的物件產生關聯 `HandleT` 。

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>參數

*h*<br/>
控制代碼。

## <a name="handletclose"></a><a name="close"></a>HandleT：： Close

關閉目前的 `HandleT` 物件。

```cpp
void Close();
```

### <a name="remarks"></a>備註

目前的基礎控制碼已 `HandleT` 關閉，而且 `HandleT` 設定為不正確狀態。

如果控制碼未正確關閉，則會在呼叫執行緒中引發例外狀況。

## <a name="handletdetach"></a><a name="detach"></a>HandleT：:D etach

解除目前 `HandleT` 物件與其基礎控制碼的的對應。

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>傳回值

基礎控制碼。

### <a name="remarks"></a>備註

當此作業完成時，目前的 `HandleT` 會設定為不正確狀態。

## <a name="handletget"></a><a name="get"></a>HandleT：： Get

取得基礎控制碼的值。

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>傳回值

控制代碼。

## <a name="handlethandle_"></a><a name="handle"></a>HandleT：： handle_

包含物件所代表的控制碼 `HandleT` 。

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlethandlet"></a><a name="handlet"></a>HandleT：： HandleT

初始化 `HandleT` 類別的新執行個體。

```cpp
explicit HandleT(
   typename HandleTraits::Type h =
      HandleTraits::GetInvalidValue()
);

HandleT(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>參數

*h*<br/>
控制代碼。

### <a name="remarks"></a>備註

第一個函 `HandleT` 式會初始化不是物件之有效控制碼的物件。 第二個函式會 `HandleT` 從參數*h*建立新的物件。

## <a name="handletinternalclose"></a><a name="internalclose"></a>HandleT：： InternalClose

關閉目前的 `HandleT` 物件。

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>傳回值

**`true`** 如果目前已 `HandleT` 成功關閉，則為，否則為 **`false`** 。

### <a name="remarks"></a>備註

`InternalClose()`為 **`protected`** 。

## <a name="handletisvalid"></a><a name="isvalid"></a>HandleT：： IsValid

指出目前的 `HandleT` 物件是否代表控制碼。

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>傳回值

**`true`** 如果 `HandleT` 代表控制碼，則為，否則為 **`false`** 。

## <a name="handletoperator"></a><a name="operator-assign"></a>HandleT：： operator =

將指定之物件的值移 `HandleT` 至目前的 `HandleT` 物件。

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>參數

*h*<br/>
控制碼的右值參考。

### <a name="return-value"></a>傳回值

目前物件的參考 `HandleT` 。

### <a name="remarks"></a>備註

此操作會使 `HandleT` 參數*h*指定的物件失效。
