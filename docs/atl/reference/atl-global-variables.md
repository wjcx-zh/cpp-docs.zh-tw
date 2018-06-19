---
title: ATL 全域變數 |Microsoft 文件
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
ms.openlocfilehash: 4664c99eb49b57f258be399c042fa14b60bbecdf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356475"
---
# <a name="atl-global-variables"></a>ATL 全域變數

## <a name="patlmodule"></a>_pAtlModule  
儲存的指標至目前模組的全域變數。  

```cpp  
__declspec(selectany) CAtlModule * _pAtlModule  
```  
### <a name="remarks"></a>備註  
這個全域變數上的方法可以用來提供 （現在已過時） 類別 CComModule 提供 Visual c + + 6.0 中的功能。

### <a name="example"></a>範例  

```cpp  
LONG lLocks = _pAtlModule->GetLockCount();  
```  
### <a name="requirements"></a>需求  
 **標頭：** atlbase.h  

