---
title: 字串化運算子 （#） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, operators
- arguments [C++], converting to strings
- stringizing operator
- preprocessor
- string literals, converting macro parameters to
- macros [C++], converting parameters to strings
- '# preprocessor operator'
ms.assetid: 1175dd19-4538-43b3-ad97-a008ab80e7b1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2bbb1aa7db586a4b45084883491c8869b434eb8b
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2018
ms.locfileid: "42538219"
---
# <a name="stringizing-operator-"></a>字串化運算子 (#)
數字符號或 「 字串化 」 的運算子 (**#**) 將巨集參數轉換為字串常值中，而不會擴充參數定義。 只會搭配接受引數的巨集使用。 如果出現在巨集定義的型式參數之前，巨集引動過程傳入的實質引數會以引號括住並且將視為字串常值。 然後字串常值會取代巨集定義中每個字串化運算子和型式參數的組合。  
  
> [!NOTE]
> ANSI C 標準的 Microsoft C (6.0 版和之前版本) 擴充功能之前會展開字串常值和字元常數中的巨集型式引數，但目前已不再支援此功能。 依賴此擴充功能的程式碼應該使用字串化改寫 (**#**) 運算子。  
  
實際引數的第一個語彙基元之前和最後一個語彙基元之後的空白字元則會予以忽略。 在實際引數中語彙基元之間的任何空白字元，在產生的字串常值中皆會縮短為單一空白字元。 因此，如果在實際引數的兩個語彙基元之間出現註解，將會縮短為單一空白字元。 產生的字串常值會自動與任何僅以空白字元分隔的相鄰字串常值串連。  
  
此外，如果通常包含引數中的字元需要逸出序列用於字串常值時 (例如引號 (**」**) 或反斜線 (**\\**) 字元)，必要的逸出反斜線字元之前，會自動插入。  
  
它搭配包含逸出序列的字串，Visual c + + 字串化運算子不會無法正確運作。 在此情況下，編譯器會產生[編譯器錯誤 C2017](../error-messages/compiler-errors-1/compiler-error-c2017.md)。  
  
## <a name="examples"></a>範例  

下列範例中展示一項巨集定義，其中包含字串化運算子和叫用巨集的主函式：  
  
這類引動過程會在前置處理期間展開並且產生下列程式碼：  
  
```cpp  
int main() {  
   printf_s( "In quotes in the printf function call\n" "\n" );  
   printf_s( "\"In quotes when printed to the screen\"\n" "\n" );  
   printf_s( "\"This: \\\" prints an escaped double quote\"" "\n" );  
}  
```  
  
```cpp  
// stringizer.cpp  
#include <stdio.h>  
#define stringer( x ) printf_s( #x "\n" )  
int main() {  
   stringer( In quotes in the printf function call );   
   stringer( "In quotes when printed to the screen" );     
   stringer( "This: \"  prints an escaped double quote" );  
}  
```  
  
```Output  
In quotes in the printf function call  
"In quotes when printed to the screen"  
"This: \"  prints an escaped double quote"  
```  
 
下列範例示範如何展開巨集參數：  
  
```cpp  
// stringizer_2.cpp  
// compile with: /E  
#define F abc  
#define B def  
#define FB(arg) #arg  
#define FB1(arg) FB(arg)  
FB(F B)  
FB1(F B)  
```  
  
## <a name="see-also"></a>另請參閱  
 
[前置處理器運算子](../preprocessor/preprocessor-operators.md)