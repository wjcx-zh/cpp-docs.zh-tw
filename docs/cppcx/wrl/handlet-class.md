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
ms.openlocfilehash: f66fbe23c305be15e09928242175dfa7ce8c141b
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821814"
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

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公用 Typedefs

Name     | 描述
-------- | -----------------------------
`Traits` | `HandleTraits` 的同義字。

### <a name="public-constructors"></a>公用建構函式

Name                                | 描述
----------------------------------- | --------------------------------------------------
[HandleT：： HandleT](#handlet)        | 初始化 `HandleT` 類別的新執行個體。
[HandleT：： ~ HandleT](#tilde-handlet) | 將 `HandleT` 類別的實例。

### <a name="public-methods"></a>公用方法

Name                         | 描述
---------------------------- | ----------------------------------------------------------------------
[HandleT：： Attach](#attach)   | 將指定的控制碼與目前的 `HandleT` 物件產生關聯。
[HandleT：： Close](#close)     | 關閉目前的 `HandleT` 物件。
[HandleT：:D etach](#detach)   | 解除目前 `HandleT` 物件與其基礎控制碼的的對應。
[HandleT：： Get](#get)         | 取得基礎控制碼的值。
[HandleT：： IsValid](#isvalid) | 指出目前的 `HandleT` 物件是否代表控制碼。

### <a name="protected-methods"></a>保護方法

Name                                     | 描述
---------------------------------------- | ------------------------------------
[HandleT：： InternalClose](#internalclose) | 關閉目前的 `HandleT` 物件。

### <a name="public-operators"></a>公用運算子

Name                                   | 描述
-------------------------------------- | ----------------------------------------------------------------------------------
[HandleT：： operator =](#operator-assign) | 將指定之 `HandleT` 物件的值移至目前的 `HandleT` 物件。

### <a name="protected-data-members"></a>受保護的資料成員

Name                        | 描述
--------------------------- | ----------------------------------------------------------------
[HandleT：： handle_](#handle) | 包含由 `HandleT` 物件表示的控制碼。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`HandleT`

## <a name="requirements"></a>需求

**標頭：** corewrappers。h

**命名空間：** Microsoft：： WRL：：包裝函式

## <a name="tilde-handlet"></a>HandleT：： ~ HandleT

將 `HandleT` 類別的實例。

```cpp
~HandleT();
```

## <a name="attach"></a>HandleT：： Attach

將指定的控制碼與目前的 `HandleT` 物件產生關聯。

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>參數

*h*<br/>
控制碼。

## <a name="close"></a>HandleT：： Close

關閉目前的 `HandleT` 物件。

```cpp
void Close();
```

### <a name="remarks"></a>備註

目前 `HandleT` 的基礎控制碼已關閉，而且 `HandleT` 設定為不正確狀態。

如果控制碼未正確關閉，則會在呼叫執行緒中引發例外狀況。

## <a name="detach"></a>HandleT：:D etach

解除目前 `HandleT` 物件與其基礎控制碼的的對應。

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>傳回值

基礎控制碼。

### <a name="remarks"></a>備註

當此作業完成時，目前的 `HandleT` 會設定為不正確狀態。

## <a name="get"></a>HandleT：： Get

取得基礎控制碼的值。

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>傳回值

控制碼。

## <a name="handle"></a>HandleT：： handle_

包含由 `HandleT` 物件表示的控制碼。

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlet"></a>HandleT：： HandleT

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
控制碼。

### <a name="remarks"></a>備註

第一個函式會初始化不是物件之有效控制碼的 `HandleT` 物件。 第二個函式會從參數*h*建立新的 `HandleT` 物件。

## <a name="internalclose"></a>HandleT：： InternalClose

關閉目前的 `HandleT` 物件。

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>傳回值

如果目前 `HandleT` 成功關閉，**則為 true** ;否則**為 false**。

### <a name="remarks"></a>備註

`InternalClose()` 為 `protected`。

## <a name="isvalid"></a>HandleT：： IsValid

指出目前的 `HandleT` 物件是否代表控制碼。

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>傳回值

如果 `HandleT` 代表控制碼，則**為 true** ;否則**為 false**。

## <a name="operator-assign"></a>HandleT：： operator =

將指定之 `HandleT` 物件的值移至目前的 `HandleT` 物件。

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>參數

*h*<br/>
控制碼的右值參考。

### <a name="return-value"></a>傳回值

目前 `HandleT` 物件的參考。

### <a name="remarks"></a>備註

此操作會使參數*h*指定的 `HandleT` 物件失效。
