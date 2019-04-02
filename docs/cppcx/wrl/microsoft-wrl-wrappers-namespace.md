---
title: Microsoft::WRL::Wrappers 命名空間
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
ms.openlocfilehash: 953318e09c4c0d00748f2b6189615dbd66677a96
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784429"
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers 命名空間

定義資源擷取為初始設定 (RAII) 包裝函式類型，可簡化物件、 字串和控制代碼的存留期管理。

## <a name="syntax"></a>語法

```cpp
namespace Microsoft::WRL::Wrappers;
```

## <a name="members"></a>成員

### <a name="typedefs"></a>Typedefs

|名稱|描述|
|----------|-----------------|
|`FileHandle`|`HandleT<HandleTraits::FileHandleTraits>`|

### <a name="classes"></a>類別

|名稱|描述|
|----------|-----------------|
|[CriticalSection 類別](criticalsection-class.md)|表示重要區段物件。|
|[事件類別 (WRL)](event-class-wrl.md)|表示事件。|
|[HandleT 類別](handlet-class.md)|物件表示的控制代碼。|
|[HString 類別](hstring-class.md)|提供對管理 HSTRING 控制代碼支援。|
|[HStringReference 類別](hstringreference-class.md)|表示從現有字串建立的 HSTRING。|
|[Mutex 類別](mutex-class.md)|表示以獨佔方式控制共用的資源的同步處理物件。|
|[RoInitializeWrapper 類別](roinitializewrapper-class.md)|初始化 Windows 執行階段。|
|[Semaphore 類別](semaphore-class.md)|表示控制項可以支援有限的數目的使用者共用的資源的同步處理物件。|
|[SRWLock 類別](srwlock-class.md)|表示輕型讀取器/寫入器鎖定。|

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](microsoft-wrl-namespace.md)