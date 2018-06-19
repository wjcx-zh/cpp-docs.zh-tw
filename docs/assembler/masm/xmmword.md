---
title: XMMWORD |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- XMMWORD
dev_langs:
- C++
helpviewer_keywords:
- XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8fd8e6c82a3275161e519eeead490473e8d64ab
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
ms.locfileid: "32056414"
---
# <a name="xmmword"></a>XMMWORD
使用 128 位元多媒體運算元的 MMX 和 SSE (XMM) 的指示。  
  
## <a name="syntax"></a>語法  
  
```  
XMMWORD  
```  
  
## <a name="remarks"></a>備註  
 `XMMWORD` 用來代表相同的型別[__m128](../../cpp/m128.md)。  
  
## <a name="example"></a>範例  
  
```  
movdqa   xmm0, xmmword ptr [ebx]  
```