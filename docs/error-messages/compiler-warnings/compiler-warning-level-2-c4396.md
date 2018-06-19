---
title: 編譯器警告 （層級 2） C4396 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4396
dev_langs:
- C++
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b937b6ecebedc6984279502a5f64b287f09bd2d9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290666"
---
# <a name="compiler-warning-level-2-c4396"></a>編譯器警告 (層級 2) C4396
'name' : 當 Friend 宣告參考函式樣板的特製化時，不能使用內嵌規範  
  
 函式樣板的特製化不能指定任何[內嵌](../../cpp/inline-functions-cpp.md)規範。 編譯器會發出警告 C4396 並忽略內嵌規範。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請從 Friend 函式宣告移除 `inline`、 `__inline`或 `__forceinline` 規範。  
  
## <a name="example"></a>範例  
 下列程式碼範例顯示無效的 Friend 函式宣告與 `inline` 規範。  
  
```  
// C4396.cpp  
// compile with: /W2 /c  
  
class X;   
template<class T> void Func(T t, int i);  
  
class X {  
    friend inline void Func<char>(char t, int i);  //C4396  
// try the following line instead  
//    friend void Func<char>(char t, int i);   
    int i;  
};  
```