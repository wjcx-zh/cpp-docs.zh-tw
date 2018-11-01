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
ms.openlocfilehash: ce904ecbd9a5855c63fd43f07f88c215cef544ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451086"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits 結構

特製化`CriticalSection`支援無效的重要區段或函式來釋放重要區段物件。

## <a name="syntax"></a>語法

```
struct CriticalSectionTraits;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱   | 描述
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | A`typedef`重要區段定義的指標。 `Type` 定義為`typedef CRITICAL_SECTION* Type;`。

### <a name="public-methods"></a>公用方法

名稱                                                       | 描述
---------------------------------------------------------- | -----------------
[Criticalsectiontraits:: Getinvalidvalue](#getinvalidvalue) | 特製化`CriticalSection`範本，讓範本不一定正確。
[Criticalsectiontraits:: Unlock](#unlock)                   | 特製化`CriticalSection`範本，因此它支援指定的重要區段物件釋放擁有權。

## <a name="inheritance-hierarchy"></a>繼承階層

`CriticalSectionTraits`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>Criticalsectiontraits:: Getinvalidvalue

特製化`CriticalSection`範本，讓範本不一定正確。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>傳回值

一律傳回無效的重要區段的指標。

### <a name="remarks"></a>備註

`Type`修飾詞指`typedef CRITICAL_SECTION* Type;`。

## <a name="unlock"></a>Criticalsectiontraits:: Unlock

特製化`CriticalSection`範本，因此它支援指定的重要區段物件釋放擁有權。

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>參數

*cs*<br/>
重要區段物件的指標。

### <a name="remarks"></a>備註

`Type`修飾詞指`typedef CRITICAL_SECTION* Type;`。

如需詳細資訊，請參閱 < **LeaveCriticalSection 函式**中**同步處理函式**Windows API 文件的章節。
