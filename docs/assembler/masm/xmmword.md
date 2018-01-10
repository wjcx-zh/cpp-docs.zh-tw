---
title: "XMMWORD |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: XMMWORD
dev_langs: C++
helpviewer_keywords: XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fa415124a11b307272305c87eabec35fafc13141
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="xmmword"></a>XMMWORD
使用 128 位元多媒體運算元的 MMX 和 SSE (XMM) 的指示。  
  
## <a name="syntax"></a>語法  
  
```  
XMMWORD  
```  
  
## <a name="remarks"></a>備註  
 `XMMWORD`用來代表相同的型別[__m128](../../cpp/m128.md)。  
  
## <a name="example"></a>範例  
  
```  
movdqa   xmm0, xmmword ptr [ebx]  
```