---
title: 編譯器警告 （層級 1） C4662 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4662
dev_langs:
- C++
helpviewer_keywords:
- C4662
ms.assetid: 7efda273-d04a-47b7-ad65-ff1ff94b5ffc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60739959a6c26e0a1674b287ebf0a4605966e09b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283422"
---
# <a name="compiler-warning-level-1-c4662"></a>編譯器警告 (層級 1) C4662
明確具現化 (Explicit Instantiation)；樣板類別 'identifier1' 沒有特製化 'identifier2' 用的定義  
  
 指定的樣板類別已宣告，但未定義。  
  
## <a name="example"></a>範例  
  
```  
// C4662.cpp  
// compile with: /W1 /LD  
template<class T, int i> class MyClass; // no definition  
template MyClass< int, 1>;              // C4662  
```