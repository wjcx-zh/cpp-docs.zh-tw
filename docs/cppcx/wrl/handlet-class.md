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
ms.openlocfilehash: bde7d7f1bd6730d96cb0f7a0d191a32eb8ed3e8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371457"
---
# <a name="handlet-class"></a>HandleT 類別

表示物件的句柄。

## <a name="syntax"></a>語法

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>參數

*處理特徵*<br/>
定義句柄的常見特徵的[HandleTraits](handletraits-structure.md)結構的實例。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱     | 描述
-------- | -----------------------------
`Traits` | `HandleTraits` 的同義字。

### <a name="public-constructors"></a>公用建構函式

名稱                                | 描述
----------------------------------- | --------------------------------------------------
[手柄T::手柄T](#handlet)        | 將 `HandleT` 類別的新執行個體初始化。
[手柄T:=手柄T](#tilde-handlet) | 取消初始化類的`HandleT`實例。

### <a name="public-methods"></a>公用方法

名稱                         | 描述
---------------------------- | ----------------------------------------------------------------------
[句柄T::附加](#attach)   | 將指定的句柄與當前`HandleT`物件關聯。
[手柄T:關閉](#close)     | 關閉目前的 `HandleT` 物件。
[手柄T::D埃塔奇](#detach)   | 將當前`HandleT`物件與其基礎句柄分離。
[句柄T:取得](#get)         | 獲取基礎句柄的值。
[句柄T:有效](#isvalid) | 指示當前`HandleT`物件是否表示句柄。

### <a name="protected-methods"></a>保護方法

名稱                                     | 描述
---------------------------------------- | ------------------------------------
[句柄T::內部關閉](#internalclose) | 關閉目前的 `HandleT` 物件。

### <a name="public-operators"></a>公用運算子

名稱                                   | 描述
-------------------------------------- | ----------------------------------------------------------------------------------
[手柄::運算符*](#operator-assign) | 將指定`HandleT`物件的值移動到`HandleT`當前 物件。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                        | 描述
--------------------------- | ----------------------------------------------------------------
[手柄::handle_](#handle) | 包含由物件表示的`HandleT`句柄。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`HandleT`

## <a name="requirements"></a>需求

**標題:** 核心包裝.h

**命名空間:** 微軟::WRL:包裝

## <a name="handlethandlet"></a><a name="tilde-handlet"></a>手柄T:=手柄T

取消初始化類的`HandleT`實例。

```cpp
~HandleT();
```

## <a name="handletattach"></a><a name="attach"></a>句柄T::附加

將指定的句柄與當前`HandleT`物件關聯。

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>參數

*H*<br/>
控制代碼。

## <a name="handletclose"></a><a name="close"></a>手柄T:關閉

關閉目前的 `HandleT` 物件。

```cpp
void Close();
```

### <a name="remarks"></a>備註

目前的基礎句柄`HandleT`已關閉`HandleT`, 並且設定為無效狀態。

如果句柄未正確關閉,則調用線程中會引發異常。

## <a name="handletdetach"></a><a name="detach"></a>手柄T::D埃塔奇

將當前`HandleT`物件與其基礎句柄分離。

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>傳回值

基礎句柄。

### <a name="remarks"></a>備註

此操作完成後,電流`HandleT`將設置為無效狀態。

## <a name="handletget"></a><a name="get"></a>句柄T:取得

獲取基礎句柄的值。

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>傳回值

控制代碼。

## <a name="handlethandle_"></a><a name="handle"></a>手柄::handle_

包含由物件表示的`HandleT`句柄。

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlethandlet"></a><a name="handlet"></a>手柄T::手柄T

將 `HandleT` 類別的新執行個體初始化。

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

*H*<br/>
控制代碼。

### <a name="remarks"></a>備註

第一個`HandleT`建構函數初始化不是物件的有效句柄的物件。 第二個建構函數從參數`HandleT` *h*創建一個新物件。

## <a name="handletinternalclose"></a><a name="internalclose"></a>句柄T::內部關閉

關閉目前的 `HandleT` 物件。

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>傳回值

**如果**`HandleT`目前 成功關閉,為 true;否則,**假**。

### <a name="remarks"></a>備註

`InternalClose()` 為 `protected`。

## <a name="handletisvalid"></a><a name="isvalid"></a>句柄T:有效

指示當前`HandleT`物件是否表示句柄。

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>傳回值

如果`HandleT`表示句柄,**則為 true;** 否則,**假**。

## <a name="handletoperator"></a><a name="operator-assign"></a>手柄::運算符*

將指定`HandleT`物件的值移動到`HandleT`當前 物件。

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>參數

*H*<br/>
對句柄的 rvalue 引用。

### <a name="return-value"></a>傳回值

對當前`HandleT`物件的引用。

### <a name="remarks"></a>備註

此操作使參數*h*`HandleT`指定的物件無效。
