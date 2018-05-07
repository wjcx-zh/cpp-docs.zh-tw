---
title: 編譯器警告 （層級 1） C4091 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4091
dev_langs:
- C++
helpviewer_keywords:
- C4091
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 79a0a74ad2cf6471679fd776f296d465ee8dd29c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4091"></a>編譯器警告 （層級 1） C4091
'keyword': 未不宣告任何變數時，忽略 'type' 的左邊  
  
 編譯器偵測到的情況下，使用者可能想要的變數宣告，但編譯器找不到宣告變數。  
  
## <a name="example"></a>範例  
 A`__declspec`使用者定義型別宣告的開頭的屬性會套用至該類型的變數。 C4091 表示沒有宣告變數時。 下列範例會產生 C4091。  
  
```  
// C4091.cpp  
// compile with: /W1 /c  
__declspec(dllimport) class X {}; // C4091  
  
// __declspec attribute applies to varX  
__declspec(dllimport) class X2 {} varX;  
  
// __declspec attribute after the class or struct keyword   
// applies to user defined type  
class __declspec(dllimport) X3 {};  
```  
  
## <a name="example"></a>範例  
 如果識別項是 typedef，它不能也是變數的名稱。 下列範例會產生 C4091。  
  
```  
// C4091_b.cpp  
// compile with: /c /W1 /WX  
#define LIST 4  
typedef struct _LIST {} LIST;   // C4091  
```