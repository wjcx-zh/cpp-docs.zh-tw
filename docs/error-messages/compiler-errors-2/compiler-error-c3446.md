---
title: 編譯器錯誤 C3446 |Microsoft 文件
ms.custom: ''
ms.date: 07/21/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3446
dev_langs:
- C++
helpviewer_keywords:
- C3445
ms.assetid: 33064548-24e4-46f1-beb1-476e3c3b3fbf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a7715ebbc094c2c3c91aa3a0bb42f7df97bef08
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3446"></a>編譯器錯誤 C3446  
  
>'*類別*': 實值類別的成員不允許的預設成員初始設定式  
  
在 Visual Studio 2015 和以前版本中，編譯器允許 (但忽略) 實值類別成員的預設成員初始設定式。 實值類別的預設初始化一律會以零初始化成員；不允許預設建構函式。 在 Visual Studio 2017 中，預設成員初始設定式會引發編譯器錯誤，如這個範例中所示︰

## <a name="example"></a>範例  
 下列範例會產生 C3446 在 Visual Studio 2017 和更新版本：  
  
```cpp  
// C3446.cpp  
value struct V
{
       int i = 0; // error C3446: 'V::i': a default member initializer  
                  // is not allowed for a member of a value class
       int j {0}; // C3446           
};
```  
  
若要更正這個錯誤，移除初始設定式：  
  
```cpp  
// C3446b.cpp  
value struct V
{
       int i;  
       int j;
};
```  
  
