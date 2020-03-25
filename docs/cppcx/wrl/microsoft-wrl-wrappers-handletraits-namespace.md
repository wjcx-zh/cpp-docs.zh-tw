---
title: Microsoft::WRL::Wrappers::HandleTraits Namespace
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
ms.openlocfilehash: b19cc426fc7c1b4fc6ec0638730d59998f8c108a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213729"
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Microsoft::WRL::Wrappers::HandleTraits Namespace

描述一般以控制碼為基礎之資源類型的特性。

## <a name="syntax"></a>語法

```cpp
namespace Microsoft::WRL::Wrappers::HandleTraits;
```

## <a name="members"></a>成員

### <a name="structures"></a>結構

|名稱|描述|
|----------|-----------------|
|[CriticalSectionTraits 結構](criticalsectiontraits-structure.md)|特製化 `CriticalSection` 物件，以支援不正確關鍵區段或釋放重要區段的函式。|
|[EventTraits 結構](eventtraits-structure.md)|定義 `Event` 類別控制碼的特性。|
|[FileHandleTraits 結構](filehandletraits-structure.md)|定義檔案控制代碼的特性。|
|[HANDLENullTraits 結構](handlenulltraits-structure.md)|定義未初始化控制碼的一般特性。|
|[HANDLETraits 結構](handletraits-structure.md)|定義控制碼的一般特性。|
|[MutexTraits 結構](mutextraits-structure.md)|定義[Mutex](mutex-class.md)類別的一般特性。|
|[SemaphoreTraits 結構](semaphoretraits-structure.md)|定義信號物件的一般特性。|
|[SRWLockExclusiveTraits 結構](srwlockexclusivetraits-structure.md)|描述獨佔鎖定模式中 `SRWLock` 類別的一般特性。|
|[SRWLockSharedTraits 結構](srwlocksharedtraits-structure.md)|描述共用鎖定模式中 `SRWLock` 類別的一般特性。|

## <a name="requirements"></a>需求

**標頭：** corewrappers。h

**命名空間：** Microsoft：： WRL：：包裝函式

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Wrappers 命名空間](microsoft-wrl-wrappers-namespace.md)
