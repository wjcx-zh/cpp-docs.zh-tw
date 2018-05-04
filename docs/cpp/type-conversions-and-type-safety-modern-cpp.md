---
title: 類型轉換和型別安全 （現代 c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 629b361a-2ce1-4700-8b5d-ab4f57b245d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13dabba7b7cfc769d91471c2dfc6f92f1b414996
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="type-conversions-and-type-safety-modern-c"></a>類型轉換和類型安全 (現代 C++)
這份文件識別常見問題的型別轉換，並說明如何避免這些在 c + + 程式碼中。  
  
 當您撰寫 c + + 程式時，務必確定它是類型安全。 這表示每個變數、 函式的引數和傳回值儲存的資料，可接受類型的函式，並牽涉到不同類型的值的作業 「 意義 」，且不會導致資料遺失，不正確的位元模式的解譯或記憶體損毀。 永遠不會明確或隱含地將值轉換從一個類型到另一個程式是安全類型所定義。 不過，類型轉換，即使是不安全的轉換，有時候是必要。 例如，您可能必須是浮動將結果儲存點類型的變數作業`int`，或您可能必須將值傳遞的不帶正負號`int`函式會採用帶正負號的`int`。 這兩個範例說明不安全的轉換，因為它們可能會造成資料遺失或值的重新解譯。  
  
 當編譯器偵測到不安全的轉換時，就會發出錯誤或警告。 錯誤停止編譯;可讓繼續的編譯警告，但指出程式碼中出現可能的錯誤。 不過，即使您的程式會編譯警告，它仍可能包含程式碼會導致不正確的結果的隱含類型轉換。 也可以明確的轉換或轉型，程式碼中的所導入型別錯誤。  
  
## <a name="implicit-type-conversions"></a>隱含類型轉換  
 當運算式中包含不同的內建類型的運算元，且沒有明確的轉換都存在時，編譯器會使用內建*標準轉換*來轉換其中一個運算元的類型相符。 有一個成功為止，編譯器會嘗試在妥善定義的序列中的轉換。 如果升級為所選取的轉換，編譯器不會發出警告。 如果縮小轉換，則編譯器會發出警告可能會遺失資料。 實際的資料遺失是否進行取決於實際值，但我們建議您將這項警告視為錯誤。 如果有相關的使用者定義型別，編譯器會嘗試使用您指定的類別定義的轉換。 如果找不到可接受的轉換，編譯器會發出錯誤，並不會編譯程式。 如需管理標準轉換的規則的詳細資訊，請參閱[標準轉換](../cpp/standard-conversions.md)。 如需使用者定義轉換的詳細資訊，請參閱[使用者定義轉換 (C + + /CLI)](../dotnet/user-defined-conversions-cpp-cli.md)。  
  
### <a name="widening-conversions-promotion"></a>擴展轉換 （升級）  
 在擴展轉換，較小的變數中的值被指派給較大且不會遺失資料的變數。 擴展轉換永遠是安全的因為編譯器會以無訊息模式執行，並不會發出警告。 下列轉換會擴展轉換。  
  
|從|以|  
|----------|--------|  
|任何帶正負號或不帶正負號整數類資料類型除外`long long`或 `__int64`|`double`|  
|`bool` 或 `char`|任何其他內建型別|  
|`short` 或 `wchar_t`|`int`, `long`, `long long`|  
|`int`, `long`|`long long`|  
|`float`|`double`|  
  
### <a name="narrowing-conversions-coercion"></a>縮小轉換 （強制型轉）  
 編譯器會隱含地執行縮小轉換，但它會警告您有關可能資料遺失。 需要這些警告很嚴重。 如果您確定會發生資料遺失的狀況，因為較大的變數中的值永遠剛好在較小的變數，然後新增明確的轉換，如此編譯器不會發出警告。 如果您不確定轉換安全，加入至您的程式碼某種類型的執行階段檢查，以處理可能會遺失資料，使它不會造成程式產生不正確的結果。 
  
 任何從浮點轉換為整數類型的型別是縮小轉換，因為浮點的小數部分點值的點會捨棄和遺失。  
  
 下列程式碼範例示範一些隱含的縮小轉換，以及它們，編譯器會發出警告。  
  
```cpp  
int i = INT_MAX + 1; //warning C4307:'+':integral constant overflow  
wchar_t wch = 'A'; //OK  
char c = wch; // warning C4244:'initializing':conversion from 'wchar_t'  
              // to 'char', possible loss of data  
unsigned char c2 = 0xfffe; //warning C4305:'initializing':truncation from  
                           // 'int' to 'unsigned char'  
int j = 1.9f; // warning C4244:'initializing':conversion from 'float' to  
              // 'int', possible loss of data  
int k = 7.7; // warning C4244:'initializing':conversion from 'double' to  
             // 'int', possible loss of data  
```  
  
### <a name="signed---unsigned-conversions"></a>簽署-不帶正負號的轉換  
 帶正負號的整數類資料類型和其不帶正負號的對應項目均相同的大小，但是在轉換值的位元模式的解譯方式則有所不同。 下列程式碼範例示範當相同的位元模式會解譯為帶正負號的值，以及不帶正負號的值時，會發生什麼事。 儲存在兩者的位元模式`num`和`num2`永遠不會變更從先前的圖例中顯示的內容。  
  
```cpp  
using namespace std;  
unsigned short num = numeric_limits<unsigned short>::max(); // #include <limits>  
short num2 = num;  
cout << "unsigned val = " << num << " signed val = " << num2 << endl;  
// Prints: unsigned val = 65535 signed val = -1  
  
// Go the other way.  
num2 = -1;  
num = num2;  
cout << "unsigned val = " << num << " signed val = " << num2 << endl;  
// Prints: unsigned val = 65535 signed val = -1  
  
```  
  
 請注意，值會解譯這兩個方向。 如果您的程式會產生奇數結果值的正負號看起來與您的預期相反，尋找帶正負號和不帶正負號的整數類資料類型之間的隱含轉換。 在下列範例中，運算式的結果 (0-1) 會隱含地轉換從`int`至`unsigned int`它會儲存在`num`。 這會導致重新解譯的位元模式。  
  
```cpp  
unsigned int u3 = 0 - 1;  
cout << u3 << endl; // prints 4294967295  
  
```  
  
 編譯器不帶正負號和不帶正負號的整數類資料類型之間的隱含轉換的相關警告。 因此，我們建議您完全避免簽署-到-不帶正負號的轉換。 如果您無法避免它們，然後加入程式碼執行階段檢查，以偵測轉換的值是否大於或等於零且小於或等於帶正負號類型的最大值。 在此範圍的值會從傳輸帶正負號不帶正負號或不帶正負號到帶正負號不被解譯。  
  
### <a name="pointer-conversions"></a>指標轉換  
 在許多運算式中，陣列中的第一個元素的指標隱含轉換的 c-style 陣列，常數轉換可能是以無訊息模式。 雖然這十分方便，所以也可能容易出錯。 例如，下列程式碼設計不良範例似乎也，並且尚未將編譯 Visual c + + 中，並產生的結果是 'p'。 首先，「 說明 」 的字串常數常值會轉換成`char*`，它會指向陣列的第一個項目，則該指標隨後會增加三個項目，讓它現在所指到最後一個項目 'p'。  
  
```cpp  
char* s = "Help" + 3;  
  
```  
  
## <a name="explicit-conversions-casts"></a>明確轉換 （轉型）  
 藉由使用轉型作業，您可以指示編譯器將某個型別的值轉換成另一種類型。 編譯器會引發錯誤在某些情況下，如果兩個型別都完全無關，但在其他情況下它將不會引發錯誤即使作業並不是類型安全。 盡量不要使用轉型，因為任何一個類型轉換成另一個是程式錯誤的潛在來源。 不過，轉換 （cast） 有時候是必要項目，而且並非所有的轉換相同危險。 一個有效使用轉型為您的程式碼會執行縮小轉換，而且您知道轉換不會導致您的程式產生不正確的結果。 實際上，這會告訴編譯器您知道您所進行的作業以及停止您終究其相關的警告。 另一個用法是從衍生指標類別轉換成指標至基底類別。 另一個用法是沒有`const`變數，以傳遞至函式需要非性質-`const`引數。 大部分的這些型別轉換作業會有一些風險。  
  
 在 c-style 程式設計中，相同的 c-style 轉型運算子用於所有類型的轉換 （cast）。  
  
```cpp  
(int) x; // old-style cast, old-style syntax  
int(x); // old-style cast, functional syntax  
  
```  
  
 C-style 轉型運算子相當於呼叫運算子 （），因此程式碼中不起眼和容易被忽略。 兩者都是不正確的因為它們是難以辨識瀏覽或搜尋，而且它們是不同足夠叫用的任何組合`static`， `const`，和`reinterpret_cast`。 找出舊樣式轉型實際上並未可能會發生困難而且容易發生錯誤。 基於這些理由，需要，轉型時，我們會建議使用下列 c + + 轉型的運算子在某些情況下會大幅多型別安全，並更明確地快速程式設計的意圖的其中一個：  
  
-   `static_cast`只會在編譯檢查的轉換時間。 `static_cast` 如果編譯器偵測到您嘗試不完全相容的類型之間轉型會傳回錯誤。 您也可以使用它來轉換之間指標至基底指標衍生，但編譯器永遠無法分辨這類轉換是否會在執行階段的安全。  
  
    ```cpp  
    double d = 1.58947;  
    int i = d;  // warning C4244 possible loss of data  
    int j = static_cast<int>(d);       // No warning.  
    string s = static_cast<string>(d); // Error C2440:cannot convert from  
                                       // double to std:string  
  
    // No error but not necessarily safe.  
    Base* b = new Base();  
    Derived* d2 = static_cast<Derived*>(b);  
  
    ```  
  
     如需詳細資訊，請參閱[static_cast](../cpp/static-cast-operator.md)。  
  
-   `dynamic_cast`指標-基底指標衍生的安全、 執行階段檢查的轉換。 A`dynamic_cast`安全比`static_cast`向下轉型，但執行階段檢查會產生額外負荷。  
  
    ```cpp  
    Base* b = new Base();  
  
    // Run-time check to determine whether b is actually a Derived*  
    Derived* d3 = dynamic_cast<Derived*>(b);  
  
    // If b was originally a Derived*, then d3 is a valid pointer.  
    if(d3)  
    {  
       // Safe to call Derived method.  
       cout << d3->DoSomethingMore() << endl;  
    }  
    else  
    {  
       // Run-time check failed.  
       cout << "d3 is null" << endl;  
    }  
  
    //Output: d3 is null;  
  
    ```  
  
     如需詳細資訊，請參閱[dynamic_cast](../cpp/dynamic-cast-operator.md)。  
  
-   `const_cast`轉型為`const`const-ness 變數，或轉換非-`const`變數`const`。 轉型`const`-使用此運算子的性質為只為容易發生錯誤時使用 c-style 轉型，不同處在於與`const-cast`您不太可能不小心執行轉換。 有時候您必須立即轉換`const`-性質的變數，例如，以傳遞`const`函式採用非變數`const`參數。 下列範例顯示如何執行這項工作。  
  
    ```cpp  
    void Func(double& d) { ... }  
    void ConstCast()  
    {  
       const double pi = 3.14;  
       Func(const_cast<double&>(pi)); //No error.  
    }  
  
    ```  
  
     如需詳細資訊，請參閱[const_cast](../cpp/const-cast-operator.md)。  
  
-   `reinterpret_cast`為之間的轉換不相關的類型例如`pointer`至`int`。  
  
    > [!NOTE]
    >  此轉換運算子不做通常與其他人，而且它具有不保證可以移植到其他編譯器。  
  
     下列範例說明如何`reinterpret_cast`不同於`static_cast`。  
  
    ```cpp  
    const char* str = "hello";  
    int i = static_cast<int>(str);//error C2440: 'static_cast' : cannot  
                                  // convert from 'const char *' to 'int'  
    int j = (int)str; // C-style cast. Did the programmer really intend  
                      // to do this?  
    int k = reinterpret_cast<int>(str);// Programming intent is clear.  
                                       // However, it is not 64-bit safe.  
  
    ```  
  
     如需詳細資訊，請參閱[reinterpret_cast 運算子](../cpp/reinterpret-cast-operator.md)。  
  
## <a name="see-also"></a>另請參閱  
 [C + + 類型系統](../cpp/cpp-type-system-modern-cpp.md)   
 [歡迎回到 c + +](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)