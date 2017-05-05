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
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: c81fc315c4bb893b96876b7b67b42806a3246583
ms.lasthandoff: 04/29/2017

---
# <a name="compiler-error-c2872"></a>編譯器錯誤 C2872
'*符號*': 模稜兩可的符號  
  
編譯器無法判斷在參考的符號。 具有指定名稱的多個符號會位於範圍內。 編譯器發現模稜兩可的符號，請參閱下列錯誤訊息，取得檔案位置和宣告的資訊。 若要修正此問題，您可以完整限定的模稜兩可的符號使用它的命名空間，例如`std::byte`或`::byte`。 您也可以使用[命名空間別名](../../cpp/namespaces-cpp.md#namespace_aliases)來釐清您的原始程式碼中的符號的使用者包含的命名空間提供方便使用簡短名稱。  
  
如果包含的標頭檔，就會發生 C2872 [using 指示詞](../../cpp/namespaces-cpp.md#using_directives)，並在後續的標頭檔中包含其中包含的型別，也在指定的命名空間`using`指示詞。 指定`using`指示詞只是在標頭檔所指定的所有之後`#include`。  
  
 如需 C2872 的詳細資訊，請參閱知識庫文章[PRB︰ 編譯器錯誤當您使用 #import Visual c + +.NET 中的 XML](http://support.microsoft.com/kb/316317)和["錯誤 C2872: 'Platform': 模稜兩可的符號"Visual Studio 2013 中使用 Windows::Foundation::Metadata 命名空間時，會產生錯誤訊息。](https://support.microsoft.com/kb/2890859)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2872，因為模稜兩可的參考對名為的變數`i`; 兩個具有相同名稱的變數是在範圍內︰  
  
```cpp  
// C2872.cpp  
// compile with: cl /EHsc C2872.cpp  
namespace A {  
   int i;  
}  
  
using namespace A;  
int i;  
int main() {  
   ::i++;   // ok, uses i from global namespace  
   A::i++;   // ok, uses i from namespace A  
   i++;   // C2872 ambiguous: ::i or A::i? 
   // To fix this issue, use the fully qualified name
   // for the intended variable. 
}  
```
