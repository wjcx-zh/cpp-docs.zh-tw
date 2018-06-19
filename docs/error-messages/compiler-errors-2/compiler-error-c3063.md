---
title: 編譯器錯誤 C3063 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3063
dev_langs:
- C++
helpviewer_keywords:
- C3063
ms.assetid: 0ecf6f1f-e4a7-487a-9fd5-79d8ac470001
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68809002b2c895387cd10d33615ec9d6c7a6b861
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33248976"
---
# <a name="compiler-error-c3063"></a>編譯器錯誤 C3063
運算子 'operator': 所有運算元必須都具有相同的列舉類型  
  
當使用列舉值的運算子，這兩個運算元必須是列舉型別。 如需詳細資訊，請參閱[如何： 定義和使用列舉，在 C + + CLI](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)。  
  
## <a name="example"></a>範例  
下列範例會產生 C3063，並示範如何修正此問題：  
  
```  
// C3063.cpp  
// compile with: /clr  
enum class E { a, b } e, mask;  
int main() {  
   if ( ( e & mask ) != 0 ) ;   // C3063 no operator!= (E, int)  
  
   if ( ( e & mask ) != E() )   // OK  
      ;  
}  
```