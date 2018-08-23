---
title: 已被取代 （C/c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.deprecated
- deprecated_CPP
dev_langs:
- C++
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d51ee23ab4e4be9cf24b913cb0c4ffa325a9bbf5
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2018
ms.locfileid: "42541181"
---
# <a name="deprecated-cc"></a>deprecated (C/C++)
**已被取代**pragma 可讓您指定的函式、 類型或任何其他識別項可能不再支援未來版本，或無法再使用。  
> [!NOTE]
> 如需 C + + 14`[[deprecated]]`屬性，且使用的時機的指引屬性與 Microsoft declspec 或 pragma，請參閱 < [c + + 標準屬性](../cpp/attributes.md)屬性。
  
## <a name="syntax"></a>語法  
  
```  
#pragma deprecated( identifier1 [,identifier2, ...] )  
```  
  
## <a name="remarks"></a>備註  
當編譯器遇到所指定的識別碼**過時**pragma，就會發出編譯器警告[C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)。   
  
您可以取代巨集名稱。 為巨集名稱加上引號，否則會發生巨集展開。  
  
因為**已被取代**pragma 適用於所有的比對識別項，並不會計入帳戶的簽章，它不是最適合的選項即將淘汰的多載函式的特定版本。 任何相符的函式名稱帶入範圍，就會觸發警告。

我們建議使用 C + + 14`[[deprecated]]`屬性，如果可能的話，而不是**已被取代**pragma。 Microsoft 專有[__declspec （deprecated)](../cpp/deprecated-cpp.md)宣告修飾詞也是較好的選擇，在許多情況下，比**已被取代**pragma。 `[[deprecated]]`屬性和`__declspec(deprecated)`修飾詞可讓您指定為特定形式的多載函式已被取代的狀態。 診斷的警告，才會出現在特定的多載函式的參考屬性或修飾詞套用至。  
  
## <a name="example"></a>範例  
  
```cpp  
// pragma_directive_deprecated.cpp  
// compile with: /W3  
#include <stdio.h>  
void func1(void) {  
}  
  
void func2(void) {  
}  
  
int main() {  
   func1();  
   func2();  
   #pragma deprecated(func1, func2)  
   func1();   // C4995  
   func2();   // C4995  
}  
```  
  
下列範例將示範如何取代類別：  
  
```cpp  
// pragma_directive_deprecated2.cpp  
// compile with: /W3  
#pragma deprecated(X)  
class X {  // C4995  
public:  
   void f(){}  
};  
  
int main() {  
   X x;   // C4995  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 
[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)