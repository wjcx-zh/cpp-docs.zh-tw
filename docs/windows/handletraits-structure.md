---
title: HANDLETraits 結構 |Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue method
ms.assetid: 22963e88-d857-4624-9182-7c986daff722
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 33181b2cf477c3f753eacf63110a426b36e62b31
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235265"
---
# <a name="handletraits-structure"></a>HANDLETraits 結構

定義通用的控制代碼的特性。

## <a name="syntax"></a>語法

```cpp
struct HANDLETraits;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱   | 描述
------ | ---------------------
`Type` | 控制代碼的同義字。

### <a name="public-methods"></a>公用方法

名稱                                              | 描述
------------------------------------------------- | -----------------------------
[Handletraits:: Close](#close)                     | 關閉指定的控制代碼。
[Handletraits:: Getinvalidvalue](#getinvalidvalue) | 表示無效的控制代碼。

## <a name="inheritance-hierarchy"></a>繼承階層

`HANDLETraits`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers::HandleTraits

## <a name="close"></a>Handletraits:: Close

關閉指定的控制代碼。

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>參數

*h*<br/>
若要關閉控制代碼。

### <a name="return-value"></a>傳回值

`true` 如果處理*h*順利完成，否則關閉`false`。

## <a name="getinvalidvalue"></a>Handletraits:: Getinvalidvalue

表示無效的控制代碼。

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>傳回值

一律會傳回 INVALID_HANDLE_VALUE。 （INVALID_HANDLE_VALUE 是由 Windows 定義）。
