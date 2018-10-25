---
title: HandleT 類別 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d0f7364ac86aebd0f5a9a1c0f7ec2343b9e162d0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081664"
---
# <a name="handlet-class"></a>HandleT 類別

物件表示的控制代碼。

## <a name="syntax"></a>語法

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>參數

*HandleTraits*<br/>
執行個體[HandleTraits](../windows/handletraits-structure.md)結構定義的控制代碼的一般特性。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱     | 描述
-------- | -----------------------------
`Traits` | `HandleTraits` 的同義字。

### <a name="public-constructors"></a>公用建構函式

名稱                                | 描述
----------------------------------- | --------------------------------------------------
[Handlet:: Handlet](#handlet)        | 初始化 `HandleT` 類別的新執行個體。
[HandleT:: ~ HandleT](#tilde-handlet) | 取消初始化的執行個體`HandleT`類別。

### <a name="public-methods"></a>公用方法

名稱                         | 描述
---------------------------- | ----------------------------------------------------------------------
[Handlet:: Attach](#attach)   | 將指定的控制代碼與目前`HandleT`物件。
[Handlet:: Close](#close)     | 關閉目前`HandleT`物件。
[Handlet:: Detach](#detach)   | 取消目前的關聯`HandleT`從其基礎控制代碼的物件。
[Handlet:: Get](#get)         | 取得基礎控制代碼的值。
[Handlet:: Isvalid](#isvalid) | 指出是否目前`HandleT`物件表示的控制代碼。

### <a name="protected-methods"></a>保護方法

名稱                                     | 描述
---------------------------------------- | ------------------------------------
[Handlet:: Internalclose](#internalclose) | 關閉目前`HandleT`物件。

### <a name="public-operators"></a>公用運算子

名稱                                   | 描述
-------------------------------------- | ----------------------------------------------------------------------------------
[Handlet:: Operator =](#operator-assign) | 將指定的值移`HandleT`物件與目前`HandleT`物件。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                        | 描述
--------------------------- | ----------------------------------------------------------------
[Handlet:: Handle_](#handle) | 包含所表示的控制代碼`HandleT`物件。

## <a name="inheritance-hierarchy"></a>繼承階層

`HandleT`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="tilde-handlet"></a>HandleT:: ~ HandleT

取消初始化的執行個體`HandleT`類別。

```cpp
~HandleT();
```

## <a name="attach"></a>Handlet:: Attach

將指定的控制代碼與目前`HandleT`物件。

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>參數

*h*<br/>
控制代碼。

## <a name="close"></a>Handlet:: Close

關閉目前`HandleT`物件。

```cpp
void Close();
```

### <a name="remarks"></a>備註

控制代碼就是目前的基礎`HandleT`已關閉，而`HandleT`設為無效的狀態。

如果控制代碼不正確關閉，就會呼叫的執行緒中引發例外狀況。

## <a name="detach"></a>Handlet:: Detach

取消目前的關聯`HandleT`從其基礎控制代碼的物件。

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>傳回值

基礎控制代碼。

### <a name="remarks"></a>備註

這項作業完成時，目前`HandleT`設為無效的狀態。

## <a name="get"></a>Handlet:: Get

取得基礎控制代碼的值。

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>傳回值

控制代碼。

## <a name="handle"></a>Handlet:: Handle_

包含所表示的控制代碼`HandleT`物件。

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlet"></a>Handlet:: Handlet

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

第一個建構函式初始化`HandleT`不是有效的控制代碼到物件的物件。 第二個建構函式會建立新`HandleT`參數中的物件*h*。

## <a name="internalclose"></a>Handlet:: Internalclose

關閉目前`HandleT`物件。

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>傳回值

**真**如果目前`HandleT`關閉順利完成，否則**false**。

### <a name="remarks"></a>備註

`InternalClose()` 為 `protected`。

## <a name="isvalid"></a>Handlet:: Isvalid

指出是否目前`HandleT`物件表示的控制代碼。

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>傳回值

**真**如果`HandleT`表示的控制代碼，否則**false**。

## <a name="operator-assign"></a>Handlet:: Operator =

將指定的值移`HandleT`物件與目前`HandleT`物件。

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>參數

*h*<br/>
右值參考的控制代碼。

### <a name="return-value"></a>傳回值

目前的參考`HandleT`物件。

### <a name="remarks"></a>備註

這項作業會導致無效`HandleT`參數所指定的物件*h*。
