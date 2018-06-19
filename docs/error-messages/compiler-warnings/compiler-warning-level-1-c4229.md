---
title: 編譯器警告 （層級 1） C4229 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4229
dev_langs:
- C++
helpviewer_keywords:
- C4229
ms.assetid: aadfc83b-1e5f-4229-bd0a-9c10a5d13182
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c902bf397d5906645a9310da337561627d7c443
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275411"
---
# <a name="compiler-warning-level-1-c4229"></a>編譯器警告 (層級 1) C4229
過時的用法： 已忽略修飾詞的資料  
  
 使用 Microsoft 修飾詞，例如`__cdecl`資料宣告為過時的作法。  
  
## <a name="example"></a>範例  
  
```  
// C4229.cpp  
// compile with: /W1 /LD  
int __cdecl counter;   // C4229 cdecl ignored  
```