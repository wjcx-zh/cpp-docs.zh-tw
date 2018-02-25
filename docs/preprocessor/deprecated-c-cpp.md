---
title: "已被取代 （C/c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a5df80fffb5b9cdeabfe19d5a5de6eb771d35d3d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="deprecated-cc"></a>deprecated (C/C++)
**取代**pragma 可讓您指出，函式、 類型或任何其他識別項可能不再支援未來版本，或應該不會再使用。  
> [!NOTE]
> 如需 C + + 14`[[deprecated]]`屬性，以及何時使用該指引屬性 vs Microsoft declspec 或 pragma，請參閱[c + + 標準屬性](../cpp/attributes2.md)屬性。
  
## <a name="syntax"></a>語法  
  
```  
#pragma deprecated( identifier1 [,identifier2, ...] )  
```  
  
## <a name="remarks"></a>備註  
 當編譯器遇到所指定的識別項**取代**pragma，就會發出編譯器警告[C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)。   
  
 您可以取代巨集名稱。 為巨集名稱加上引號，否則會發生巨集展開。  
  
 因為**取代**pragma 適用於所有符合的識別項，而且不會計入帳戶的簽章，無法淘汰的多載函式的特定版本的最佳選項。 帶入範圍觸發程序警告任何比對函式名稱。

  我們建議您在使用 C + + 14`[[deprecated]]`屬性，如果可能的話，而不是**取代**pragma。 Microsoft 專有[__declspec （deprecated)](../cpp/deprecated-cpp.md)宣告修飾詞也是較佳的選擇，在許多情況下，比**取代**pragma。 `[[deprecated]]`屬性和`__declspec(deprecated)`修飾詞可讓您指定特定形式的多載函式已被取代的狀態。 診斷的警告，才會出現在特定的多載函式的參考屬性或修飾詞套用至。  
  
## <a name="example"></a>範例  
  
```  
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
  
```  
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
  
## <a name="see-also"></a>請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)