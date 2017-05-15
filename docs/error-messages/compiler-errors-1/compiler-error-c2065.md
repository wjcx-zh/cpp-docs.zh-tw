---
title: "編譯器錯誤 C2065 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2065
dev_langs:
- C++
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: 5a3a0d4389a958f421f23a4dc96a395eaf3e22ab
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="compiler-error-c2065"></a>編譯器錯誤 C2065
'identifier'：未宣告的識別項  
  
編譯器找不到識別項的宣告。 如果識別項是變數，您必須指定變數的類型，在宣告中才可以使用即可。 函式名稱識別項時，此函數會使用的參數必須指定在宣告中，才能使用此函式。 如果識別項是使用者定義型別的標記，例如`class`或`struct`，必須先宣告的標記類型，才能使用。 類型別名識別項時，必須使用宣告的型別`using`宣告或`typedef`之前，可以使用類型。  
  
有許多可能的原因造成此錯誤。 以下是一些最常見的問題︰
  
## <a name="example-misspelled-identifier"></a>範例︰ 拼錯的識別項  
  
識別項名稱的拼字錯誤，或識別項使用了錯誤的大寫和小寫字母時，通常就會發生這個錯誤。 宣告中的名稱必須完全符合您使用的名稱。  
  
```cpp  
// C2065_spell.cpp  
// compile with: cl /EHsc C2065_spell.cpp 
#include <iostream> 
using namespace std; 
int main() { 
    int someIdentifier = 42; 
    cout << "Some Identifier: " << SomeIdentifier << endl;   
    // C2065: 'SomeIdentifier': undeclared identifier 
    // To fix, correct the spelling:  
    // cout << "Some Identifier: " << someIdentifier << endl;   
}  
```
  
## <a name="example-missing-header-file"></a>範例︰ 遺漏標頭檔  
  
您不包含標頭檔宣告識別項。 請確定檔案包含的識別項的宣告包含使用它的每個原始程式檔中。  
  
```cpp  
// C2065_header.cpp  
// compile with: cl /EHsc C2065_spell.cpp 

//#include <stdio.h> 
int main() { 
    fpos_t file_position = 42; // C2065: 'fpos_t': undeclared identifier 
    // To fix, uncomment the #include <stdio.h> line
    // to include the header where fpos_t is defined  
} 
```  
  
您可能會看到此錯誤在 Windows 桌面應用程式原始程式檔，如果您定義`VC_EXTRALEAN`， `WIN32_LEAN_AND_MEAN`，或`WIN32_EXTRA_LEAN`。 這些前置處理器巨集排除某些標頭檔從 windows.h 和 afxv\_w32.h 來加速編譯。 查看 windows.h 和 afxv_w32.h 所排除的最新描述。  
  
## <a name="eample-missing-closing-quote"></a>Eample︰ 遺漏右引號  
  
如果您遺漏右引號字串常數之後，就會發生此錯誤。 這是容易混淆編譯器。 
  
```cpp  
// C2065_quote.cpp  
// compile with: cl /EHsc C2065_quote.cpp 
#include <iostream>  

int main() { 
    // Fix this issue by adding the closing quote to "Aaaa"
    char * first = "Aaaa, * last = "Zeee"; 
    std::cout << "Name: " << first 
        << " " << last << std::endl; // C2065: 'last': undeclared identifier 
} 
```  
  
## <a name="example-use-iterator-outside-for-loop-scope"></a>範例︰ 使用 for 迴圈範圍之外的迭代器  
  
如果您宣告中的迭代器變數，會發生此錯誤`for`迴圈，然後再嘗試使用該迭代器變數的範圍外`for`迴圈。 可讓編譯器[/zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)預設編譯器選項。 請參閱[偵錯迭代器支援](../../standard-library/debug-iterator-support.md)如需詳細資訊。  
  
```cpp  
// C2065_iter.cpp  
// compile with: cl /EHsc C2065_iter.cpp 
#include <iostream> 
#include <string> 

int main() {
    // char last = '!'; 
    std::string letters{ "ABCDEFGHIJKLMNOPQRSTUVWXYZ" }; 
    for (const char& c : letters) {
        if ('Q' == c) {
            std::cout << "Found Q!" << std::endl;
        }
        // last = c;
    }
    std::cout << "Last letter was " << c << std::endl; // C2065
    // Fix by using a variable declared in an outer scope.
    // Uncomment the lines that declare and use 'last' for an example.
    // std::cout << "Last letter was " << last << std::endl; // C2065
} 
```  
  
## <a name="example-preprocessor-removed-declaration"></a>範例︰ 前置處理器已移除的宣告  
  
如果您參考的函式或變數，就不會編譯您的目前組態的有條件地編譯程式碼中，會發生此錯誤。 如果您目前不支援您的建置環境中的標頭檔中呼叫的函式時，這也會發生。 如果特定變數或函式只可用在定義特定的前置處理器巨集時，，請確定定義相同的前置處理器巨集時，可以只編譯呼叫這些函式的程式碼。 因為如果未定義必要的前置處理器巨集的目前組建組態，灰色函式的宣告，此問題很容易在 IDE 中，找出。  
  
這是當您建置在偵錯，但是不零售可運作的程式碼範例︰  
  
```cpp  
// C2065_defined.cpp
// Compile with: cl /EHsc /W4 /MT C2065_defined.cpp
#include <iostream>
#include <crtdbg.h>
#ifdef _DEBUG
    _CrtMemState oldstate;
#endif
int main() {
    _CrtMemDumpStatistics(&oldstate); 
    std::cout << "Total count " << oldstate.lTotalCount; // C2065
    // Fix by guarding references the same way as the declaration:
    // #ifdef _DEBUG
    //    std::cout << "Total count " << oldstate.lTotalCount;
    // #endif
}
```
  
## <a name="example-use-an-unscoped-identifier"></a>範例︰ 使用不限範圍的識別項  
  
如果您的識別項的範圍不正確，就會發生此錯誤。 例如，c + + 標準程式庫函式和運算子不完整的命名空間，，或您不帶`std`到目前的範圍使用的命名空間`using`指示詞，編譯器找不到它們。 若要修正此問題，您必須完整限定識別項名稱，或指定命名空間與`using`指示詞。  
  
此範例無法編譯，因為`cout`和`endl`中定義`std`命名空間︰  
  
```cpp  
// C2065_scope.cpp  
// compile with: cl /EHsc C2065_scope.cpp 
// using namespace std;   // Uncomment this line to fix  
#include <iostream>  
int main() {  
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier 
                               // C2065 'endl': undeclared identifier
    // Or try the following line instead  
    std::cout << "Hello" << std::endl;  
}
```  
  
在宣告的識別項`class`， `struct`，或`enum class`型別，也必須在封入範圍的名稱所限定。
  
## <a name="example-ccli-type-deduction-failure"></a>範例︰ C + + CLI 類型推斷失敗  
  
如果無法從使用的參數推論預定的型別引數，當呼叫泛型函式，會發生此錯誤。 如需詳細資訊，請參閱[泛型函式 (C + + /CLI)](../../windows/generic-functions-cpp-cli.md)。  
  
```cpp  
// C2065_b.cpp  
// compile with: /clr  
generic <typename ItemType>  
void G(int i) {}  
  
int main() {  
   // global generic function call  
   G<T>(10);   // C2065  
   G<int>(10);   // OK - fix with a specific type argument  
}  
```  
  
## <a name="example-ccli-attribute-parameters"></a>範例︰ C + + CLI 屬性參數  
  
針對 Visual C++ 2005 所進行的編譯器一致性工作，也可能會導致這個錯誤：Visual C++ 屬性的參數檢查。  
  
```cpp  
// C2065_attributes.cpp  
// compile with: cl /c /clr C2065_attributes.cpp  
[module(DLL, name=MyLibrary)];   // C2065  
// try the following line instead  
// [module(dll, name="MyLibrary")];  
  
[export]  
struct MyStruct {  
   int i;  
};  
```  

