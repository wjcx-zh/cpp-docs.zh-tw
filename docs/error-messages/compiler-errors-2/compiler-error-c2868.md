---
title: 編譯器錯誤 C2868 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2868
dev_langs:
- C++
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84465453ca7a1d76a9dd6b199232384c2ef9124b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2868"></a>編譯器錯誤 C2868  
  
> '*識別碼*': using 宣告不合法語法; 預期的限定名稱  
  
A [using 宣告](../../cpp/using-declaration.md)需要*限定的名稱*，範圍運算子 (`::`) 分隔的命名空間、 類別或列舉型別名稱的結尾是識別項名稱的順序。 單一的範圍解析運算子可能用於全域命名空間中導入的名稱。  
  
## <a name="example"></a>範例  
  
下列範例會產生 C2868，並也會顯示正確的使用方式：  
  
```cpp  
// C2868.cpp  
class X {  
public:  
   int i;  
};  
  
class Y : X {  
public:  
   using X::i;   // OK  
};  
  
int main() {  
   using X;   // C2868  
}  
```