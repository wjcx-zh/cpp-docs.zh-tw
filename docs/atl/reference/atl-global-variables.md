---
title: ATL 全域變數
ms.date: 12/06/2017
f1_keywords:
- ATLBASE/_pAtlModule
helpviewer_keywords:
- global variables, ATL
- _pAtlModule
ms.assetid: e881a319-99ca-4f5d-8a0b-34b3dcd0f37f
ms.openlocfilehash: 4f98b31d2454b7c6e903e5b5b87bceb4ddcb6961
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498315"
---
# <a name="atl-global-variables"></a>ATL 全域變數

## <a name="patlmodule"></a>_pAtlModule

全域變數，儲存在目前模組的指標。

```cpp
__declspec(selectany) CAtlModule * _pAtlModule
```

### <a name="remarks"></a>備註

這個全域變數上的方法可用來提供 （現在已過時） 的 CComModule 類別提供在 Visual c + + 6.0 的功能。

### <a name="example"></a>範例

```cpp
LONG lLocks = _pAtlModule->GetLockCount();
```

### <a name="requirements"></a>需求

**標頭：** atlbase.h
