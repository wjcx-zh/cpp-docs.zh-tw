---
title: HANDLENullTraits 結構
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue method
ms.assetid: 88a29a14-c516-40cb-a0ca-ee897a668623
ms.openlocfilehash: a7ce730b8d723a839c5b509c825cff84111ca613
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226915"
---
# <a name="handlenulltraits-structure"></a>HANDLENullTraits 結構

定義未初始化控制碼的一般特性。

## <a name="syntax"></a>語法

```cpp
struct HANDLENullTraits;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱   | 說明
------ | ---------------------
`Type` | 控制碼的同義字。

### <a name="public-methods"></a>公用方法

名稱                                                  | 說明
----------------------------------------------------- | -----------------------------
[HANDLENullTraits：： Close](#close)                     | 關閉指定的控制碼。
[HANDLENullTraits：： GetInvalidValue](#getinvalidvalue) | 表示不正確控制碼。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`HANDLENullTraits`

## <a name="requirements"></a>需求

**標頭：** corewrappers。h

**命名空間：** Microsoft：： WRL：：包裝函式：： HandleTraits

## <a name="handlenulltraitsclose"></a><a name="close"></a>HANDLENullTraits：： Close

關閉指定的控制碼。

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>參數

*h*<br/>
要關閉的控制碼。

### <a name="return-value"></a>傳回值

**`true`** 如果控制碼*h*成功關閉，則為，否則為 **`false`** 。

## <a name="handlenulltraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>HANDLENullTraits：： GetInvalidValue

表示不正確控制碼。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>傳回值

一律會傳回 **`nullptr`** 。
