---
title: 編譯器警告 （層級 3） C4359 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4359
dev_langs:
- C++
helpviewer_keywords:
- C4359
ms.assetid: d8fe993c-ef82-45a0-a43d-c29f9d1bacdb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7ddc48294734e5a180014ea20cf98b9d7374f25
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292980"
---
# <a name="compiler-warning-level-3-c4359"></a>編譯器警告 (層級 3) C4359
'type': 實際對齊 (8) 大於 __declspec(align()) 中指定的值  
  
 指定類型的對齊小於其資料成員的其中一個類型的對齊方式。  如需詳細資訊，請參閱[對齊](../../cpp/align-cpp.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4359。  
  
```  
// C4359.cpp  
// compile with: /W3 /c  
struct __declspec(align(8)) C8 { __int64 i; };  
struct __declspec(align(4)) C4  { C8 m8; };   // C4359  
struct __declspec(align(8)) C8_b  { C8 m8; };   // OK  
struct __declspec(align(16)) C16  { C8 m8; };   // OK  
```