---
title: "constexpr （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- constexpr_cpp
dev_langs:
- C++
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cf1094be23074fe71e65a3077de51263f01a81c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="constexpr-c"></a>constexpr (C++)
關鍵字 `constexpr` 是在 C++11 中引進，並在 C++14 中改進。 這表示*常數運算式*。 就像 `const`，它可以套用至變數，以便在任何程式碼嘗試修改值時引發編譯器錯誤。 不同於 `const` 的是，`constexpr` 也可以套用至函式和類別建構函式。 `constexpr` 表示值或傳回值為常數，而且可能的話，會在編譯時期計算。  只要在需要 const 整數 (例如在樣板引數和陣列宣告中) 之處，便可以使用 `constexpr` 整數值。 而且，當可以計算出的值，而不是執行階段編譯時期，它可讓您的程式更快速執行並使用較少的記憶體。  
  
## <a name="syntax"></a>語法  
  
```cpp  
constexpr  literal-type  identifier = constant-expression;
constexpr  literal-type  identifier { constant-expression };
constexpr literal-type identifier(params );
constexpr ctor (params);  
```  
  
#### <a name="parameters"></a>參數  
 `params`  
 一或多個必須是常值類型 (如下所示) 且本身是常數運算式的參數。  
  
## <a name="return-value"></a>傳回值  
 Constexpr 變數或函式必須傳回下列常值類型之一。  
  
## <a name="literal-types"></a>常值類型  
 為了限制運算編譯時期常數的複雜性，及其可能造成的編譯時間影響，C++14 標準要求參與常數運算式的類型必須受限為常值類型。 常值類型的配置可以在編譯時期決定。 以下是常值類型：  
  
1.  void  
  
2.  純量類型  
  
3.  參考  
  
4.  Void、純量類型或參考的陣列  
  
5.  具有 trivial 解構函式和一或多個非移動或複製建構函式之 constexpr 建構函式的類別。 此外，其所有的非靜態資料成員和基底類別必須是常值類型，且不會變動。  
  
## <a name="constexpr-variables"></a>constexpr 變數  
 const 和 constexpr 變數之間的主要差異是 const 變數的初始化可以延遲到執行階段，而 constexpr 變數則必須在編譯時期初始化。  所有的 constexpr 變數都是常數。  

-  如果變數具有常值類型並已初始化，則可以使用 `constexpr` 宣告。 如果是由建構函式執行初始化，則建構函式必須宣告為 `constexpr`。  
  
-   如果所參考的物件已由常數運算式初始化，而且在初始化期間叫用的任何隱含轉換也是常數運算式，則參考可以宣告為 constexpr。  
  
-   `constexpr` 變數或函式的所有宣告必須具有 `constexpr` 指定名稱。  
  
 
  
 
  
```cpp  
constexpr float x = 42.0;  
constexpr float y{108};  
constexpr float z = exp(5, 3);  
constexpr int i; // Error! Not initialized  
int j = 0;  
constexpr int k = j + 1; //Error! j not a constant expression  
```  
  
## <a name="constexpr-functions"></a>constexpr 函式  
 `constexpr` 函式的傳回值，可以在耗用程式碼需要它時，在編譯時進行計算。  當其引數為 `constexpr` 值，而且耗用程式碼在編譯時期需要傳回值 (例如初始化 `constexpr` 變數)，或提供非類型樣板引數，便會產生編譯時期常數。 當呼叫時使用了非`constexpr` 引數，或在編譯時期不需要其值時，便會像一般函式一樣在執行階段產生值。  (這種雙行為讓您不必撰寫相同函式的 `constexpr` 和非 `constexpr` 版本。)  
 
 `constexpr` 函式或建構函式隱含即為 `inline`。 
 
 下列規則適用於 constexpr 函式：

- `constexpr` 函式必須只接受並傳回常值類型。 

- `constexpr` 函式可以是遞迴的。 

- 它不能[虛擬](../cpp/virtual-cpp.md)。 建構函式不能定義為 constexpr 封入類別有任何虛擬基底類別。

- 主體可以定義為 `= default` 或 `= delete`。 

- 主體不可以包含`goto`陳述式或 try 區塊。 

- 非 constexpr 範本的明確特製化可以宣告為 `constexpr`：  
  
- `constexpr` 範本的明確特製化不需要也是 `constexpr`： 


<!--conformance note-->
下列規則適用於在 Visual Studio 2017 和更新版本的 constexpr 函式： 

- 它可能包含如果和切換陳述式，以及所有迴圈陳述式，包括以範圍為基礎，時，且請勿-時
    
- 它可能包含本機變數宣告，但變數必須進行初始化、 必須是常值型別，而且不能是靜態或執行緒區域。 在本機宣告的變數不需要是 const，可能會變動。

- Constexpr 非靜態成員函式不需要為 const 隱含。

  
```cpp  
constexpr float exp(float x, int n)  
{  
    return n == 0 ? 1 :  
        n % 2 == 0 ? exp(x * x, n / 2) :  
        exp(x * x, (n - 1) / 2) * x;  
};  
```  
  
> [!TIP]
>  注意：在 Visual Studio 偵錯工具中，您可以藉由在函式中放入中斷點，來分辨 `constexpr` 函式是否會在編譯時期評估。 如果叫用中斷點，便已在執行階段呼叫此函式。  否則便是在編譯時期呼叫函式。  
  
 
## <a name="example"></a>範例  
 下列範例會顯示 `constexpr` 變數、函式及使用者定義類型。 請注意，在 main() 最後一個陳述式中，因為不需要在編譯時間知道其值，所以`constexpr` 成員函式 Getvalue() 是執行階段呼叫。  
  
```  
#include <iostream>  
  
using namespace std;  
  
// Pass by value   
constexpr float exp(float x, int n)  
{  
    return n == 0 ? 1 :  
        n % 2 == 0 ? exp(x * x, n / 2) :  
        exp(x * x, (n - 1) / 2) * x;  
};  
  
// Pass by reference  
constexpr float exp2(const float& x, const int& n)  
{  
    return n == 0 ? 1 :  
        n % 2 == 0 ? exp2(x * x, n / 2) :  
        exp2(x * x, (n - 1) / 2) * x;  
};  
  
// Compile time computation of array length  
template<typename T, int N>  
constexpr int length(const T(&ary)[N])   
{   
    return N;   
}   
  
// Recursive constexpr function  
constexpr int fac(int n)  
{   
    return n == 1 ? 1 : n*fac(n - 1);   
}  
  
// User-defined type  
class Foo  
{  
public:  
    constexpr explicit Foo(int i) : _i(i) {}  
    constexpr int GetValue()  
    {  
        return _i;  
    }  
private:  
    int _i;  
};  
  
int main()  
{  
    //foo is const:  
    constexpr Foo foo(5);   
    // foo = Foo(6); //Error!  
  
    //Compile time:  
    constexpr float x = exp(5, 3);   
    constexpr float y { exp(2, 5) };  
    constexpr int val = foo.GetValue();   
    constexpr int f5 = fac(5);  
    const int nums[] { 1, 2, 3, 4 };  
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };  
  
    //Run time:   
    cout << "The value of foo is " << foo.GetValue() << endl;   
  
}  
  
```  
  
## <a name="requirements"></a>需求  
 Visual Studio 2015  
  
## <a name="see-also"></a>請參閱  
 [宣告和定義](../cpp/declarations-and-definitions-cpp.md)   
 [const](../cpp/const-cpp.md)