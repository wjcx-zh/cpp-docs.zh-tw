---
title: "類型轉換和類型安全 (現代 C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 629b361a-2ce1-4700-8b5d-ab4f57b245d5
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 類型轉換和類型安全 (現代 C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此文件列出一般型別轉換的問題並說明如何在 C\+\+ 程式碼中避免此類情型。  
  
 當您撰寫 C \+\+ 程式時，確認為型別安全這一點很重要。  這表示每個變數、函式引數以及函式回傳值存取一種接受資料，此操作包含使不同型別的值合乎規範，並避免資料遺失、位元組合的誤譯和記憶體損毀。  根據定義，不論指令明確與否，程式無法任意轉換型別中的值即為型別安全。  然而，在某些情況下，即使為不安全的型別轉換，仍需要做型別轉換。  舉例來說，有時候你必須要將浮點數的運算結果存入  `int`的變數之中，或者將不帶正負號的 `int` 型別中的值，傳入帶正負號的 `int`型別變數中。  上述的例子皆說明不安全的型別轉換，因為它們可能導致資料值的遺失或重新定義其值。  
  
 當編譯器偵測到不安全的型別轉換時，便會發出錯誤或警告。  當發生錯誤時則停止編譯，警告則不停止，雖然警告允許繼續編譯，卻顯示程式碼中含有可能會發生的錯誤。  但是，即使程式在編譯過程中沒有發出警告訊息，程式中仍可能包含因隱含型別轉換而產生的錯誤結果。  程式中也有可能因為明確的型別轉換或轉型而導致型別錯誤。  
  
## 隱含型別轉換  
 當一運算式中含有不同型別的運算元，且沒有任何明確的轉型，編譯器會利用內建的 *轉換標準* 將其中一個運算元轉換成相符的型別。  編譯器會在運算成功時，停止嘗試型別轉換。  如果為晉升的型別轉換，此時編譯器不會發出警告。  但如果為窄型的轉換，則編譯器會警告可能發生資料遺失。  實際上，資料是否遺失，取決於目前所包含的值，但不論情況為何，仍建議將此警告視為錯誤。  如果牽涉至使用者定義型別時。編譯器會嘗試使用您在類別定義中所指定的轉換。  當無法找到可行的轉換，編譯器會發出錯誤，並停止編譯程式。  如需標準轉換規則的詳細資訊，請參閱 [標準轉換](../cpp/standard-conversions.md)。  如需使用者定義型別轉換的詳細資訊，請參閱[使用者定義轉換](../dotnet/user-defined-conversions-cpp-cli.md)。  
  
### 擴展轉換 \(晉升\)  
 在擴展轉換中，較小變數中的值會指派至較大的變數，且不會發生資料遺失。  因為擴展轉換必定為安全的型別轉換，編譯器會自動執行轉換且不發出警告訊息。  下列的型別轉換屬於擴展轉換。  
  
|從|轉換為|  
|-------|---------|  
|任何帶正負號或不帶正負號的整數類資料型別 \(不包含 `long long` 和 `__int64` \)|`double`|  
|`bool` 或 `char`|內建型別|  
|`short` 或 `wchar_t`|`int`, `long`, `long long`|  
|`int`, `long`|`long long`|  
|`float`|`double`|  
  
### 窄型轉換 \(強制轉型\)  
 編譯器默認執行的窄型轉換，但仍會發出可能導致資料遺失的警告訊息。  請謹慎評估這些警告訊息。  當您確定因較大變數的值必定符合較小變數的規格，所以不會發生資料遺失時，請添加明確轉換的指令，讓編譯器停止發出警告訊息。  但如果你無法確定型別轉換是否安全，將執行階段檢查加入程式碼中，以處理可能發生的資料遺失，讓程式不會產生錯誤結果。  如需如何處理這種情況的建議，請參閱 [\(NOTINBUILD\)How to: Handle Narrowing Conversions \(C\+\+\)](http://msdn.microsoft.com/zh-tw/e483237e-501e-4a12-ac24-51526f6ddeaa)。  
  
 因為浮點數值的分數部分被捨棄，從浮點型別轉換為整數型別皆為窄型轉換。  
  
 下列範例程式碼顯示了隱含窄型轉換以及編譯器對此所發出的警告。  
  
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
  
### 帶正負號\-不帶正負號的型別轉換  
 帶正負號和不帶正負號的資料型別恆為相同大小，其差別在於位元組合對於轉換後所得值的不同解譯。  下列範例程式碼展示同樣的位元組合，如何在帶正負號型別和不帶正負號型別中的值中解譯。  `num` 和 `num2` 中的位元組合值在儲存之後皆不再改變。  
  
```cpp  
  
using namespace std;  
unsigned short num = numeric_limits<unsigned short>::max(); // #include <limits>  
short num2 = num;  
cout << "unsigned val = " << num << " signed val = " << num2 << endl;  
// Prints: unsigned val = 65535 signed val = -1  
  
// Go the other way.  
num2 = -1;  
num = num2;  
cout << "unsigned val = " << num << " signed val = " << num2 << endl;  
// Prints: unsigned val = 65535 signed val = -1  
  
```  
  
 請注意值在兩條路徑中皆重新定義。  如果值的正負號與你預期的結果不同，請在程式中尋找是否發生隱含帶正負號—不帶正負號的整數型別轉換。  在下列範例中，當運算式 \(0– 1\) 的結果從 `int` 型別儲存至 `num` 中時，發生隱含轉換至 `unsigned int` 型別的過程。  而這會導致此位元組合重新定義。  
  
```cpp  
  
unsigned int u3 = 0 - 1;  
cout << u3 << endl; // prints 4294967295  
  
```  
  
 編譯器不會發出帶正負號和不帶正負號間整數型別隱含轉換的警告訊息。  因此，建議您儘可能避免帶正負號和不帶正負號間的型別轉換。  如果無法避免此狀況，則請將執行階段檢查加入至程式碼中，以檢查轉換的值是否大於或等於零，且小於或等於帶正負號型別的最大值。  在此範圍內的值，若發生帶正負號、不帶正負號型別的轉換，則不用重新定義。  
  
### 指標轉換  
 C 樣式在許多運算式中，會將陣列隱含轉換至第一個元素的指標，因此，陣列發生常數型別轉換時，不會發出警告訊息。  雖然這很方便，但卻容易發生錯誤。  例如，下列設計的程式碼看似毫無意義，卻仍能在 Visual C\+\+ 中編譯並產生「p」的結果。  首先，「Help」字串常數被轉換為指向第一個元素的 `char*` 指標，接下來此指標增加了3個單位，因此指標最後會指向最後一個元素「p」。  
  
```cpp  
  
char* s = "Help" + 3;  
  
```  
  
## 明確型別轉換 \(轉型\)  
 使用轉型作業，可以指示編譯器將一個型別的值轉換至另一個型別。  編譯器在兩型別完全無關的狀況下會發生錯誤，但在某些情況下，即使不是型別安全的運作，也不會發出錯誤訊息。  請謹慎使用轉型，因為任何型別的轉換有可能是來源程式的錯誤。  不過，並非所有的轉型都同樣危險，仍然會有必要轉型的時機。  利用轉型的其中一個用途為在您確定轉換不會發生錯誤時，執行窄型轉換。  實際上，這會告訴編譯器您了解程式運行的過程，並停止發出警告訊息。  另一個用途是從衍生類別指標轉型至基底類別指標。  以及轉型成非 `const` 型別的變數，並將此變數傳至限定非`const` 型別引數的函式。  大部分轉型作業含有潛在的風險。  
  
 同一轉型運算子在 C\-style 程式中可為所有的轉型所使用。  
  
```cpp  
  
(int) x; // old-style cast, old-style syntax  
int(x); // old-style cast, functional syntax  
  
```  
  
 因為 C\-style 轉型運算子與呼叫運算子相同，所以容易在程式碼中被忽略。  當兩者同時發生錯誤時，難以一眼就辨識出或搜尋得到，且因本質上的差異，而難與 `static`、 `const`和 `reinterpret_cast` 做搭配。  舊式的型別轉換不僅理解困難且容易發生錯誤。  基於這些原因，如果需要轉型，請利用下列所列的 C\+\+ 轉型運算子，在某些情況下較為型別安全，且清楚表示程式的設計目的：  
  
-   `static_cast` 只檢查在編譯時期的轉換。  如果編譯器偵測到將完全不相容的型別進行轉型，則 `static_cast` 回傳錯誤。  你也可以利用它進行基底指標和衍生指標之前的轉型，不過編譯器不會每一次都提示何種轉型在執行階段是安全的。  
  
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
  
     如需更多詳細資訊，請參閱[靜態建構函式](../cpp/static-cast-operator.md)。  
  
-   `dynamic_cast` 在執行階段檢查基底指標轉型至衍生指標是否安全。  `dynamic_cast` 比要向下轉換的 `static_cast` 具有安全性，但在執行階段檢查會產生額外的負荷。  
  
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
  
     如需詳細資訊，請參閱 [dynamic\_cast](../cpp/dynamic-cast-operator.md)。  
  
-   `const_cast` 將變數中  `const` 型別的性質丟棄，或將非 `const` 型別變數轉型成 `const` 型別。  除非和 `const-cast` 型別一同使用，否則利用此運算子丟棄  `const` 型別的性質，將和 C\-style 之轉型一樣容易出錯。  有時候必須丟棄變數中  `const` 型別的性質，舉例來說，需要將 `const` 傳遞至限定接受非 `const` 型別參數的函式。  下列範例顯示如何執行這項工作。  
  
    ```cpp  
  
    void Func(double& d) { ... }  
    void ConstCast()  
    {  
       const double pi = 3.14;  
       Func(const_cast<double&>(pi)); //No error.  
    }  
  
    ```  
  
     如需詳細資訊，請參閱 [\/testcontainer](../cpp/const-cast-operator.md)。  
  
-   `reinterpret_cast` 用於不相關型別間的轉型，例如將 `pointer` 型別轉型至 `int` 型別。  
  
    > [!NOTE]
    >  此轉型運算子相較其他類較為少用，且不一定能在其他編譯器上使用。  
  
     以下範例說明 `reinterpret_cast` 與 `static_cast` 之間的不同。  
  
    ```cpp  
  
    const char* str = "hello";  
    int i = static_cast<int>(str);//error C2440: 'static_cast' : cannot  
                                  // convert from 'const char *' to 'int'  
    int j = (int)str; // C-style cast. Did the programmer really intend  
                      // to do this?  
    int k = reinterpret_cast<int>(str);// Programming intent is clear.  
                                       // However, it is not 64-bit safe.  
  
    ```  
  
     如需詳細資訊，請參閱[reinterpret\_cast 運算子](../cpp/reinterpret-cast-operator.md)。  
  
## 請參閱  
 [C\+\+ 類型系統](../cpp/cpp-type-system-modern-cpp.md)   
 [歡迎回到 C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)   
 [C\+\+ Standard Library](../standard-library/cpp-standard-library-reference.md)