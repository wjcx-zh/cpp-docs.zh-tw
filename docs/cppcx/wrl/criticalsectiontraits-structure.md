---
title: CriticalSectionTraits 結構
ms.date: 09/26/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock method
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
ms.openlocfilehash: 05c93bf6a2765bd11489075067c627ab3c3ab691
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372573"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits 結構

專門化`CriticalSection`物件以支援無效的關鍵部分或釋放關鍵部分的函數。

## <a name="syntax"></a>語法

```
struct CriticalSectionTraits;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱   | 描述
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | 定義`typedef`指向關鍵節的指標的 。 `Type` 定義為 `typedef CRITICAL_SECTION* Type;`。

### <a name="public-methods"></a>公用方法

名稱                                                       | 描述
---------------------------------------------------------- | -----------------
[關鍵節特徵::獲取無效值](#getinvalidvalue) | 專門化`CriticalSection`範本,以便範本始終無效。
[臨界截面:解鎖](#unlock)                   | 專門化`CriticalSection`範本,以便它支援釋放指定關鍵節物件的擁有權。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CriticalSectionTraits`

## <a name="requirements"></a>需求

**標題:** 核心包裝.h

**命名空間:** 微軟::WRL:包裝::處理特徵

## <a name="criticalsectiontraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>關鍵節特徵::獲取無效值

專門化`CriticalSection`範本,以便範本始終無效。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>傳回值

始終返回指向無效關鍵部分的指標。

### <a name="remarks"></a>備註

修飾`Type`定義為`typedef CRITICAL_SECTION* Type;`。

## <a name="criticalsectiontraitsunlock"></a><a name="unlock"></a>臨界截面:解鎖

專門化`CriticalSection`範本,以便它支援釋放指定關鍵節物件的擁有權。

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>參數

*cs*<br/>
指向關鍵截面物件的指標。

### <a name="remarks"></a>備註

修飾`Type`定義為`typedef CRITICAL_SECTION* Type;`。

有關詳細資訊,請參閱 Windows API 文件的**同步函數**部份中的 **「Leave 關鍵」節功能**。
