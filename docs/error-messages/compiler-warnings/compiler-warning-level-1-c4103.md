---
title: 編譯器警告 （層級 1） C4103 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4103
dev_langs:
- C++
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f072db4a260d2c83d1dd4b373630cd6e585efc2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4103"></a>編譯器警告 （層級 1） C4103
'filename': 對齊之後包含標頭，變更可能是因為缺少 #pragma pack(pop)  
  
 封裝會影響的類別、 配置和常見的是，如果封裝標頭檔之間的變更，可能有問題。  
  
 使用 #pragma[套件](../../preprocessor/pack.md)(pop) 前結束標頭檔，若要解決這個警告。  
  
 下列範例會產生 C4103:  
  
```  
// C4103.h  
#pragma pack(push, 4)  
  
// defintions and declarations  
  
// uncomment the following line to resolve  
// #pragma pack(pop)  
```  
  
 然後，  
  
```  
// C4103.cpp  
// compile with: /LD /W1  
#include "c4103.h"   // C4103  
```