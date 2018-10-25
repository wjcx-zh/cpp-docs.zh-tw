---
title: TerminateMap 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
dev_langs:
- C++
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bc5aec34177572552d119df967c9d25571b6cb63
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066028"
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
A[模組](../windows/module-class.md)。

*伺服器名稱*<br/>
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

[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)