---
title: "naked （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- naked_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: daa03ee746de422f96e8f39dc451a71da2e0259c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="naked-c"></a>naked (C++)
**Microsoft 特定的**  
  
 函式宣告與`naked`屬性，編譯器會產生不具初構和終解程式碼的程式碼。 利用此功能就可以使用內嵌組合語言程式碼撰寫您自己的初構/終解程式碼序列。 naked 函式在撰寫虛擬裝置驅動程式方面特別實用。  請注意，`naked`屬性只適用於 x86 和 ARM 上與並不適用於[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
__declspec(naked) declarator  
```  
  
## <a name="remarks"></a>備註  
 因為`naked`屬性僅適用於函式的定義，而且不是型別修飾詞，naked 函式必須使用擴充的屬性語法和[__declspec](../cpp/declspec.md)關鍵字。  
  

 編譯器無法產生 naked 屬性，以標記的函式的內嵌函式，即使函式也標記著[__forceinline](inline-functions-cpp.md)關鍵字。  

  
 編譯器會發出錯誤`naked`屬性會套用至非成員方法的定義以外的任何項目。  
  
## <a name="examples"></a>範例  
 此程式碼定義的函式`naked`屬性：  
  
```  
__declspec( naked ) int func( formal_parameters ) {}  
```  
  
 或者，或者：  
  
```  
#define Naked __declspec( naked )  
Naked int func( formal_parameters ) {}  
```  
  
 `naked` 屬性只會影響編譯器針對函式的初構和終解序列產生程式碼的本質。 它不會影響針對呼叫這類函式所產生的程式碼。 因此，`naked` 屬性不會視為函式類型的一部分，而且函式指標不能有 `naked` 屬性。 此外，`naked` 屬性無法套用至資料定義。 例如，此程式碼範例會產生錯誤：  
  
```  
__declspec( naked ) int i;       // Error--naked attribute not  
                                 // permitted on data declarations.  
```  
  
 `naked` 屬性只與函式的定義相關，而且無法在函式的原型中指定。 例如，這個宣告會產生編譯器錯誤：  
  
```  
__declspec( naked ) int func();  // Error--naked attribute not   
                                 // permitted on function declarations  
```  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [__declspec](../cpp/declspec.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [Naked 函式呼叫](../cpp/naked-function-calls.md)