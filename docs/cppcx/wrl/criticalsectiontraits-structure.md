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
ms.openlocfilehash: 3573cad21734a97629cbc12b76d73b99024cbc2f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220505"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits 結構

將物件特製化 `CriticalSection` ，以支援不正確重要區段，或用來釋放重要區段的函式。

## <a name="syntax"></a>語法

```
struct CriticalSectionTraits;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱   | 說明
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | **`typedef`**，定義關鍵區段的指標。 `Type` 定義為 `typedef CRITICAL_SECTION* Type;`。

### <a name="public-methods"></a>公用方法

名稱                                                       | 說明
---------------------------------------------------------- | -----------------
[CriticalSectionTraits：： GetInvalidValue](#getinvalidvalue) | 將範本特製化， `CriticalSection` 讓範本永遠無效。
[CriticalSectionTraits：： Unlock](#unlock)                   | 特製化 `CriticalSection` 範本，使其支援釋放指定之重要區段物件的擁有權。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CriticalSectionTraits`

## <a name="requirements"></a>需求

**標頭：** corewrappers。h

**命名空間：** Microsoft：： WRL：：包裝函式：： HandleTraits

## <a name="criticalsectiontraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>CriticalSectionTraits：： GetInvalidValue

將範本特製化， `CriticalSection` 讓範本永遠無效。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>傳回值

一律會傳回無效重要區段的指標。

### <a name="remarks"></a>備註

`Type`修飾詞會定義為 `typedef CRITICAL_SECTION* Type;` 。

## <a name="criticalsectiontraitsunlock"></a><a name="unlock"></a>CriticalSectionTraits：： Unlock

特製化 `CriticalSection` 範本，使其支援釋放指定之重要區段物件的擁有權。

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>參數

*cs*<br/>
關鍵區段物件的指標。

### <a name="remarks"></a>備註

`Type`修飾詞會定義為 `typedef CRITICAL_SECTION* Type;` 。

如需詳細資訊，請參閱 Windows API 檔的**同步處理函數**一節中的**LeaveCriticalSection**函式。
