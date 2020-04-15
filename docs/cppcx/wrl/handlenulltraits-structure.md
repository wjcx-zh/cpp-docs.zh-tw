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
ms.openlocfilehash: 41e06cc50f36a077a34d992c416a543e5bf9b593
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371469"
---
# <a name="handlenulltraits-structure"></a>HANDLENullTraits 結構

定義未初始化句柄的常見特徵。

## <a name="syntax"></a>語法

```cpp
struct HANDLENullTraits;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱   | 描述
------ | ---------------------
`Type` | HANDLE 的同義詞。

### <a name="public-methods"></a>公用方法

名稱                                                  | 描述
----------------------------------------------------- | -----------------------------
[操作無效:關閉](#close)                     | 關閉指定的句柄。
[操作無效:取得無效值](#getinvalidvalue) | 表示無效的句柄。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`HANDLENullTraits`

## <a name="requirements"></a>需求

**標題:** 核心包裝.h

**命名空間:** 微軟::WRL:包裝::處理特徵

## <a name="handlenulltraitsclose"></a><a name="close"></a>操作無效:關閉

關閉指定的句柄。

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>參數

*H*<br/>
要關閉的句柄。

### <a name="return-value"></a>傳回值

如果句柄*h*成功關閉,**則為 true;** 否則,**假**。

## <a name="handlenulltraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>操作無效:取得無效值

表示無效的句柄。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>傳回值

永遠會傳回 `nullptr`。
