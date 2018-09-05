---
title: ATL 全域變數 |Microsoft Docs
ms.custom: ''
ms.date: 12/06/2017
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATLBASE/_pAtlModule
dev_langs:
- C++
helpviewer_keywords:
- global variables, ATL
- _pAtlModule
ms.assetid: e881a319-99ca-4f5d-8a0b-34b3dcd0f37f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 55844390b872cb0d94ff991ab79b8519388d009f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762456"
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

