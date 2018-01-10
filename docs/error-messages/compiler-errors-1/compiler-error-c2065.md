---
title: "編譯器錯誤 C2065 |Microsoft 文件"
ms.custom: 
ms.date: 09/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2065
dev_langs: C++
helpviewer_keywords: C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5dec660bd2f47cb1e95569ced6bead2dd42fc2da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2065"></a>編譯器錯誤 C2065

> '*識別碼*': 未宣告的識別項  
  
編譯器找不到識別項的宣告。 有許多可能的原因造成此錯誤。 C2065 最常見原因有尚未被宣告的識別項、 識別項是否拼字錯誤，在宣告識別項的標頭未包含在檔案中，或是識別項遺漏範圍限定詞，比方說，`cout`而不是`std::cout`. 如需 c + + 中宣告的詳細資訊，請參閱[宣告和定義 （c + +）](../../cpp/declarations-and-definitions-cpp.md)。
  
以下是更詳細的一些常見的問題和解決方案。

## <a name="the-identifier-is-undeclared"></a>識別項未宣告

如果識別碼的變數或函式名稱，您必須將它宣告才能使用。 可使用此函式之前的函式宣告也必須包含其參數的類型。 如果變數使用宣告`auto`，編譯器必須能夠推斷其初始設定式中的型別。

如果識別項是類別或結構的成員或命名空間中宣告，它必須以限定的類別或結構名稱或命名空間名稱時結構、 類別或命名空間範圍外使用。 或者，命名空間必須以帶入範圍`using`指示詞，例如`using namespace std;`，或成員名稱必須帶入範圍`using`宣告，例如`using std::string;`。 否則，不合格的名稱會被視為目前的範圍中的宣告識別項。

如果識別項是使用者定義型別的標記，例如`class`或`struct`，必須先宣告的標記類型，才能使用。 例如，宣告`struct SomeStruct { /*...*/ };`必須先建立您可以將變數宣告`SomeStruct myStruct;`程式碼中。

類型別名識別項時，必須使用宣告的型別`using`宣告或`typedef`才能使用它。 例如，您必須宣告`using my_flags = std::ios_base::fmtflags;`才能夠使用`my_flags`做為類型別名`std::ios_base::fmtflags`。
  
## <a name="example-misspelled-identifier"></a>範例： 拼錯的識別項  
  
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
  
## <a name="example-use-an-unscoped-identifier"></a>範例： 使用不限範圍的識別項 
  
如果您的識別項的範圍不正確，就會發生此錯誤。 如果當您使用時，請參閱 C2065 `cout`，這是可能的原因。 當 c + + 標準程式庫函式和運算子不完整的命名空間，或您不帶`std`到目前的範圍使用的命名空間`using`指示詞，編譯器找不到它們。 若要修正此問題，您必須完整限定識別項名稱，或指定命名空間與`using`指示詞。  
  
此範例無法編譯，因為`cout`和`endl`中定義`std`命名空間：  
  
```cpp  
// C2065_scope.cpp  
// compile with: cl /EHsc C2065_scope.cpp
#include <iostream>  
// using namespace std;   // Uncomment this line to fix  

int main() {  
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier 
                               // C2065 'endl': undeclared identifier
    // Or try the following line instead  
    std::cout << "Hello" << std::endl;  
}
```  
  
在宣告的識別項`class`， `struct`，或`enum class`型別必須也由其封閉範圍名稱所限定，使用該範圍內時。
  
## <a name="example-missing-header-file"></a>範例： 遺漏標頭檔  
  
您不包含標頭檔宣告識別項。 請確定檔案包含的識別項的宣告包含使用它的每個原始程式檔中。  
  
```cpp  
// C2065_header.cpp  
// compile with: cl /EHsc C2065_header.cpp 

//#include <stdio.h> 
int main() { 
    fpos_t file_position = 42; // C2065: 'fpos_t': undeclared identifier 
    // To fix, uncomment the #include <stdio.h> line
    // to include the header where fpos_t is defined  
} 
```  

另一個可能的原因是如果您使用初始設定式清單不包括\<initializer_list > 標頭。

```cpp  
// C2065_initializer.cpp  
// compile with: cl /EHsc C2065_initializer.cpp 

// #include <initializer_list> 
int main() { 
    for (auto strList : {"hello", "world"})
        if (strList == "hello") // C2065: 'strList': undeclared identifier 
            return 1; 
    // To fix, uncomment the #include <initializer_list> line
} 
```  
  
您可能會看到此錯誤在 Windows 桌面應用程式原始程式檔，如果您定義`VC_EXTRALEAN`， `WIN32_LEAN_AND_MEAN`，或`WIN32_EXTRA_LEAN`。 這些前置處理器巨集排除某些標頭檔從 windows.h 和 afxv\_w32.h 來加速編譯。 查看 windows.h 和 afxv_w32.h 所排除的最新描述。  
  
## <a name="example-missing-closing-quote"></a>範例： 遺漏右引號  
  
如果您遺漏右引號字串常數之後，就會發生此錯誤。 這是容易混淆編譯器。 請注意遺漏右引號可能幾行之前報告的錯誤的位置。 
  
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
  
## <a name="example-use-iterator-outside-for-loop-scope"></a>範例： 使用 for 迴圈範圍之外的迭代器  
  
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
  
## <a name="example-preprocessor-removed-declaration"></a>範例： 前置處理器已移除的宣告  
  
如果您參考的函式或變數，就不會編譯您的目前組態的有條件地編譯程式碼中，會發生此錯誤。 如果您目前不支援您的建置環境中的標頭檔中呼叫的函式時，這也會發生。 如果特定變數或函式只可用在定義特定的前置處理器巨集時，，請確定定義相同的前置處理器巨集時，可以只編譯呼叫這些函式的程式碼。 因為如果未定義必要的前置處理器巨集的目前組建組態，灰色函式的宣告，此問題很容易在 IDE 中，找出。  
  
這是當您建置在偵錯，但是不零售可運作的程式碼範例：  
  
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
  
## <a name="example-ccli-type-deduction-failure"></a>範例： C + + CLI 類型推斷失敗  
  
如果無法從使用的參數推論預定的型別引數，當呼叫泛型函式，會發生此錯誤。 如需詳細資訊，請參閱[泛型函式 (C + + /CLI)](../../windows/generic-functions-cpp-cli.md)。  
  
```cpp  
// C2065_b.cpp  
// compile with: cl /clr C2065_b.cpp 
generic <typename ItemType>  
void G(int i) {}  
  
int main() {  
   // global generic function call  
   G<T>(10);     // C2065  
   G<int>(10);   // OK - fix with a specific type argument  
}  
```  
  
## <a name="example-ccli-attribute-parameters"></a>範例： C + + CLI 屬性參數  
  
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
