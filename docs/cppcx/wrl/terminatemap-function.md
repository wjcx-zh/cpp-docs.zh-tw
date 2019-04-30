---
title: TerminateMap 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: 2a451bf68bfb543ee5e82a9a48097cac7e8a9821
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398117"
---
# <a name="terminatemap-function"></a>TerminateMap 函式

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
inline bool TerminateMap(
   _In_ ModuleBase *module,
   _In_opt_z_ const wchar_t *serverName,
    bool forceTerminate) throw()
```

### <a name="parameters"></a>參數

*module*<br/>
A[模組](module-class.md)。

*serverName*<br/>
名稱參數所指定的模組中的 class factory 的子集*模組*。

*forceTerminate*<br/>
**true**終止類別處理站，不論它們是作用中;**false**未終止的 class factory，如果任何 factory 已啟用。

## <a name="return-value"></a>傳回值

**真**終止，否則所有的 class factory 一樣**false**。

## <a name="remarks"></a>備註

關閉指定的模組中的 class factory。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](microsoft-wrl-details-namespace.md)