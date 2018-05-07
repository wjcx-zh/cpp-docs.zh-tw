---
title: 編譯器警告 （層級 4） C4459 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4459
dev_langs:
- C++
helpviewer_keywords:
- C4459
ms.assetid: ee9f6287-9c70-4b10-82a0-add82a13997f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 93bdbfe6cceff664e7b7a5f8cee20e8df51e2fb4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4459"></a>編譯器警告 （層級 4） C4459
  
> 宣告的 '*識別碼*' 會隱藏全域宣告
  
宣告*識別碼*在區域範圍會隱藏相同名稱的宣告*識別碼*在全域範圍內。 這項警告可讓您知道要參考*識別碼*在這個範圍中解析的區域宣告的版本不通用版本，可能會或可能不到您的意圖。 一般而言，我們建議您減少為理想設計做法是使用全域變數。 若要降到最低的全域命名空間的侵害，建議使用具名命名空間的全域變數。  
  
這項警告是一項新的 Visual Studio 2015 中 Visual c + + 編譯器版本 18.00 中。 若要隱藏警告的編譯器或更新版本移轉您的程式碼時，該版本中，使用[/Wv:18](../../build/reference/compiler-option-warning-level.md)編譯器選項。 

## <a name="example"></a>範例
  
 下列範例會產生 C4459:  
  
```cpp  
// C4459_hide.cpp
// compile with: cl /W4 /EHsc C4459_hide.cpp
int global_or_local = 1;

int main() { 
    int global_or_local; // warning C4459 
    global_or_local = 2;
} 
```  
  
若要修正此問題的一種方式為建立您的全域命名空間，但不是使用`using`指示詞，將該命名空間帶入範圍內，因此所有參考都必須都使用明確限定名稱：  
  
```cpp  
// C4459_namespace.cpp
// compile with: cl /W4 /EHsc C4459_namespace.cpp
namespace globals {
    int global_or_local = 1;
}

int main() { 
    int global_or_local; // OK 
    global_or_local = 2;
    globals::global_or_local = 3;
} 
```  
