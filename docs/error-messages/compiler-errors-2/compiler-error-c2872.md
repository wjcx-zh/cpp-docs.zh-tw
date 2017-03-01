---
title: "編譯器錯誤 C2872 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2872
dev_langs:
- C++
helpviewer_keywords:
- C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 65e7a7bd56096fbeec61b651ab494d82edef9c90
ms.openlocfilehash: d53dbd9429ba3c1a525b85a3ef9f2e70152ddfa2
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2872"></a>編譯器錯誤 C2872
'symbol': 模稜兩可的符號  
  
編譯器無法判斷在參考的符號。  
  
如果包含的標頭檔，就會發生 C2872 [using 指示詞](../../cpp/namespaces-cpp.md#using_directives)，後續的標頭檔會包含和它包含也會在指定的命名空間中的類型`using`指示詞。 指定`using`指示詞只是在標頭檔所指定的所有之後`#include`。  
  
 如需 C2872 的詳細資訊，請參閱知識庫文件[PRB︰ 編譯器錯誤當您使用 #import Visual c + +.NET 中的 XML](http://support.microsoft.com/kb/316317)和[」 錯誤 C2872: '平台': 模稜兩可的符號 」 錯誤訊息，當您使用 Visual Studio 2013 Windows::Foundation::Metadata 命名空間](https://support.microsoft.com/kb/2890859)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2872:  
  
```cpp  
// C2872.cpp  
namespace A {  
   int i;  
}  
  
using namespace A;  
int i;  
int main() {  
   ::i++;   // ok  
   A::i++;   // ok  
   i++;   // C2872 ::i or A::i?  
}  
```
