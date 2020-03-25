---
title: TerminateMap 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: 560f563e43fc8b818b04cd0bda6b01fbc916cb84
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213547"
---
# <a name="terminatemap-function"></a>TerminateMap 函式

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
inline bool TerminateMap(
   _In_ ModuleBase *module,
   _In_opt_z_ const wchar_t *serverName,
    bool forceTerminate) throw()
```

### <a name="parameters"></a>參數

*name*<br/>
[模組](module-class.md)。

*serverName*<br/>
參數*模組*所指定的模組中，class factory 子集的名稱。

*forceTerminate*<br/>
**true**表示終止 class factory，不論它們是否為作用中;**false**表示如果有任何處理站在使用中，則不會終止 class factory。

## <a name="return-value"></a>傳回值

如果所有 class factory 都已終止，則為**true** ;否則**為 false**。

## <a name="remarks"></a>備註

關閉指定模組中的 class factory。

## <a name="requirements"></a>需求

**標頭：** module. h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](microsoft-wrl-details-namespace.md)
