---
title: MMWORD |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- MMWORD
dev_langs:
- C++
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e97b1e58116d633519b1a780928e05862ac1771d
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
ms.locfileid: "32054776"
---
# <a name="mmword"></a>MMWORD
用於 64 位元多媒體運算元的 MMX 和 SSE (XMM) 的指示。  
  
## <a name="syntax"></a>語法  
  
```  
MMWORD  
```  
  
## <a name="remarks"></a>備註  
 `MMWORD` 是一種。  之前新增至 MASM MMWORD，對等的功能可能已實現與：  
  
```  
mov mm0, qword ptr [ebx]  
```  
  
 這兩個指示工作在 64 位元運算元上時`QWORD`是 64 位元不帶正負號整數的類型和`MMWORD`是 64 位元的多媒體值的類型。  
  
 `MMWORD` 用來代表相同的型別[__m64](../../cpp/m64.md)。  
  
## <a name="example"></a>範例  
  
```  
movq     mm0, mmword ptr [ebx]  
```