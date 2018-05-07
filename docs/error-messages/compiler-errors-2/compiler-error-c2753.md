---
title: 編譯器錯誤 C2753 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2753
dev_langs:
- C++
helpviewer_keywords:
- C2753
ms.assetid: 92bfeeac-524a-4a8e-9a4f-fb8269055826
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acbf5736c7c263293bc1c2782cab7df4f0af2083
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2753"></a>編譯器錯誤 C2753
'*範本*': 部分特製化不能符合主要樣板的引數清單  
  
 如果樣板引數清單符合參數清單，則編譯器會將它視為相同的範本。 不允許兩次定義相同的範本。  
  
## <a name="example"></a>範例
 下列範例會產生 C2753，並示範如何修正此問題：  
  
```cpp  
// C2753.cpp  
// compile with: cl /c C2753.cpp
template<class T>  
struct A {};  
  
template<class T>  
struct A<T> {};   // C2753  
// try the following line instead  
// struct A<int> {};  
  
template<class T, class U, class V, class W, class X>  
struct B {};  
```