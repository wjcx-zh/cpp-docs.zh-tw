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
ms.openlocfilehash: d70425f414b998eb67e3937c2c126dd3eda0c00d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398377"
---
# <a name="handlenulltraits-structure"></a>HANDLENullTraits 結構

定義未初始化的控制代碼的一般特性。

## <a name="syntax"></a>語法

```cpp
struct HANDLENullTraits;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱   | 描述
------ | ---------------------
`Type` | 控制代碼的同義字。

### <a name="public-methods"></a>公用方法

名稱                                                  | 描述
----------------------------------------------------- | -----------------------------
[HANDLENullTraits::Close](#close)                     | 關閉指定的控制代碼。
[HANDLENullTraits::GetInvalidValue](#getinvalidvalue) | 表示無效的控制代碼。

## <a name="inheritance-hierarchy"></a>繼承階層

`HANDLENullTraits`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers::HandleTraits

## <a name="close"></a>HANDLENullTraits::Close

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

**真**如果處理*h*關閉順利完成，否則**false**。

## <a name="getinvalidvalue"></a>HANDLENullTraits::GetInvalidValue

表示無效的控制代碼。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>傳回值

一律傳回 `nullptr`。
