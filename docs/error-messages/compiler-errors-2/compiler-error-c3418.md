---
title: 編譯器錯誤 C3418 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3418
dev_langs:
- C++
helpviewer_keywords:
- C3418
ms.assetid: 54042c04-3c45-41c1-bad7-90f9ee05a21b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92147a636ff1b087134dd7c2d3fdbdb1398d5135
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256633"
---
# <a name="compiler-error-c3418"></a>編譯器錯誤 C3418
不支援存取規範 'specifier'  
  
CLR 存取規範指定不正確。  如需詳細資訊，請參閱類型可視性和中的成員可視性[如何： 定義與使用類別和結構 (C + + /CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)。  
  
## <a name="example"></a>範例  
下列範例會產生 C3418：  
  
```cpp  
// C3418.cpp  
// compile with: /clr /c  
ref struct m {  
internal public:   // C3418  
   void test(){}  
};  
  
ref struct n {  
internal:   // OK  
   void test(){}  
};  
```