---
title: HANDLETraits 結構
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue method
ms.assetid: 22963e88-d857-4624-9182-7c986daff722
ms.openlocfilehash: c04e53789fd737b12ca10ef2c279a05fb43f5925
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212991"
---
# <a name="handletraits-structure"></a>HANDLETraits 結構

定義控制碼的一般特性。

## <a name="syntax"></a>語法

```cpp
struct HANDLETraits;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱   | 說明
------ | ---------------------
`Type` | 控制碼的同義字。

### <a name="public-methods"></a>公用方法

名稱                                              | 說明
------------------------------------------------- | -----------------------------
[HANDLETraits：： Close](#close)                     | 關閉指定的控制碼。
[HANDLETraits：： GetInvalidValue](#getinvalidvalue) | 表示不正確控制碼。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`HANDLETraits`

## <a name="requirements"></a>需求

**標頭：** corewrappers。h

**命名空間：** Microsoft：： WRL：：包裝函式：： HandleTraits

## <a name="handletraitsclose"></a><a name="close"></a>HANDLETraits：： Close

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

## <a name="handletraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>HANDLETraits：： GetInvalidValue

表示不正確控制碼。

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>傳回值

一律會傳回 INVALID_HANDLE_VALUE。 （INVALID_HANDLE_VALUE 是由 Windows 所定義）。
