---
title: Microsoft::WRL::Wrappers 命名空間
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
ms.openlocfilehash: ece26b3f9928d44a593de830cf8a25c57e4c2d89
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213742"
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers 命名空間

定義資源取得是初始化（RAII）包裝函式類型，可簡化物件、字串和控制碼的存留期管理。

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
|[CriticalSection 類別](criticalsection-class.md)|表示重要的區段物件。|
|[事件類別 (WRL)](event-class-wrl.md)|表示事件。|
|[HandleT 類別](handlet-class.md)|表示物件的控制碼。|
|[HString 類別](hstring-class.md)|提供操作 HSTRING 控制碼的支援。|
|[HStringReference 類別](hstringreference-class.md)|表示從現有字串建立的 HSTRING。|
|[Mutex 類別](mutex-class.md)|表示專門控制共用資源的同步處理物件。|
|[RoInitializeWrapper 類別](roinitializewrapper-class.md)|初始化 Windows 執行階段。|
|[Semaphore 類別](semaphore-class.md)|表示同步處理物件，控制可支援有限使用者數目的共用資源。|
|[SRWLock 類別](srwlock-class.md)|表示超薄讀取器/寫入器鎖定。|

## <a name="requirements"></a>需求

**標頭：** corewrappers。h

**命名空間：** Microsoft：： WRL：：包裝函式

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](microsoft-wrl-namespace.md)
