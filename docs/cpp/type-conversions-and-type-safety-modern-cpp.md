---
title: 類型轉換和型別安全 （現代 c + +） |Microsoft Docs
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
ms.openlocfilehash: 9fb13c8c4ce2705d3e7af8ca5b4cd0e4b97b13ca
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059086"
---
# <a name="type-conversions-and-type-safety-modern-c"></a>類型轉換和類型安全 (現代 C++)

這份文件找出常見的類型轉換問題，並說明如何避免它們在您的 c + + 程式碼。

當您撰寫 c + + 程式時，務必確保它是型別安全。 這表示每個變數、 函式引數和函式傳回值會儲存可接受的一種資料，並牽涉到不同類型的值的作業 「 意義 」，而且不會造成資料遺失，不正確解譯位元模式，或記憶體損毀。 永遠不會明確或隱含地將值轉換的型別到另一個程式是型別安全的定義。 不過，類型轉換，甚至是不安全的轉換，有時候是必要。 比方說，您可能要儲存的浮點結果點類型的變數中的作業**int**，或者您可能必須將值傳遞的不帶正負號**int**來接受帶正負號的函式**int**。這兩個範例說明不安全的轉換，因為它們會造成資料遺失或值的重新解譯。

當編譯器偵測到不安全的轉換時，就會發出錯誤或警告。 錯誤會使編譯; 停止警告可讓繼續的編譯，但表示可能的錯誤，程式碼中。 不過，即使程式編譯而不發出警告，它仍可能包含程式碼會導致隱含型別轉換產生不正確的結果。 藉由明確的轉換或轉型，程式碼中的，也可能引入型別錯誤。

## <a name="implicit-type-conversions"></a>隱含類型轉換

當運算式中包含了屬於不同的內建類型的運算元，且沒有明確的轉型都存在時，編譯器會使用內建*標準轉換*來轉換其中一個運算元，使類型相符。 編譯器會嘗試在一系列定義完善的轉換，直到成功為止。 如果升級為所選取的轉換，編譯器不會發出警告。 如果縮小轉換，編譯器會發出有關可能會遺失資料的警告。 是否發生實際的資料遺失取決於所涉及的實際值，但我們建議此警告視為錯誤。 如果牽涉到的使用者定義型別，編譯器會嘗試使用您已在類別定義中指定的轉換。 如果找不到可接受的轉換，編譯器會發出錯誤，並不會編譯程式。 如需管理標準的轉換規則的詳細資訊，請參閱[標準轉換](../cpp/standard-conversions.md)。 如需有關使用者定義轉換的詳細資訊，請參閱 <<c0> [ 使用者定義的轉換 (C + + /cli CLI)](../dotnet/user-defined-conversions-cpp-cli.md)。

### <a name="widening-conversions-promotion"></a>擴展轉換 （升級）

擴展轉換，在較小的變數中的值會指派至較大的變數，其不會遺失資料。 擴展轉換永遠是安全的因為編譯器會以無訊息模式執行，並不會發出警告。 下列轉換會擴展轉換。

|從|以|
|----------|--------|
|任何帶正負號或不帶正負號整數類資料類型除外**長長**或 **__int64**|**double**|
|**bool**或**char**|任何其他內建類型|
|**簡短**或**wchar_t**|**int**，**長**， **long long**|
|**int**，**長**|**long long**|
|**float**|**double**|

### <a name="narrowing-conversions-coercion"></a>縮小轉換 （強制型轉）

編譯器會隱含地執行縮小轉換，但它會警告您有關潛在資料遺失。 需要這些警告非常嚴重。 如果您確定不會遺失資料，會發生，因為較大的變數中的值一律會納入較小的變數，然後加入明確的轉換，使編譯器不再會發出警告。 如果您不確定轉換是安全，新增您的程式碼某種類型的執行階段檢查，以處理可能會遺失資料，使它不會造成您的程式產生不正確的結果。

任何自浮點數轉換為整數類型的類型是縮小轉換，因為浮點的小數部分的點值的點是捨棄，而且會遺失。

下列程式碼範例示範一些隱含的縮小轉換和它們，編譯器會發出警告。

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

### <a name="signed---unsigned-conversions"></a>帶正負號的不帶正負號的轉換

帶正負號的整數類資料類型和其不帶正負號的對應項目一律是相同的大小，但它們的差異中的值轉換的位元模式的解譯方式。 下列程式碼範例示範當相同的位元模式會解譯為帶正負號的值，以及不帶正負號的值時，會發生什麼事。 儲存在兩者的位元模式`num`和`num2`永遠不會變更從較早的圖例中顯示的內容。

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

請注意，值會以兩個方向陣。 如果您的程式會產生奇怪的結果正負號的值看起來與您的預期反轉，尋找帶正負號和不帶正負號的整數類資料類型之間的隱含轉換。 在下列範例中，運算式的結果 (0-1) 會隱含地轉換從**int**要**不帶正負號的 int**它會儲存在`num`。 這會導致重新解譯位元模式。

```cpp
unsigned int u3 = 0 - 1;
cout << u3 << endl; // prints 4294967295
```

編譯器不會警告有關帶正負號和不帶正負號的整數類資料類型之間的隱含轉換。 因此，我們建議您完全避免簽署-至-不帶正負號的轉換。 如果您無法避免，然後將您的程式碼執行階段檢查，以偵測要轉換的值是否大於或等於零且小於或等於帶正負號類型的最大值。 在此範圍中的值會從傳輸簽署不帶正負號或不帶正負號到帶正負號不在陣。

### <a name="pointer-conversions"></a>指標轉換

在許多運算式，C 樣式陣列會隱含地轉換陣列中的第一個元素的指標，常數轉換可能會以無訊息方式發生。 雖然這十分方便，也很容易出錯。 比方說，下列的設計不良的程式碼範例似乎無意義，並且尚未在 Visual c + + 中會編譯，並產生 'p' 的結果。 首先，將 [說明] 字串常數常值轉換成`char*`指向陣列的第一個項目，該指標會增加三個項目，讓它現在所指向的最後一個項目 'p'。

```cpp
char* s = "Help" + 3;
```

## <a name="explicit-conversions-casts"></a>明確轉換 （轉換）

藉由使用轉型作業，您可以指示編譯器將某一型別的值轉換成其他型別。 編譯器會引發錯誤在某些情況下，如果兩個型別完全無關，但在其他情況下它將不會引發錯誤即使作業不是型別安全。 盡量不要使用轉型，因為任何一個類型轉換成另一個是程式錯誤的潛在來源。 不過，轉換 （cast） 有時是必要的而且並非所有的轉換 （cast） 也同樣的危險。 一個有效地使用轉型時，您的程式碼會執行縮小轉換，而且您知道轉換時不會導致您的程式產生不正確的結果。 實際上，這會告訴編譯器，您就會知道您的情況並停止您終究有其相關的警告。 另一個用法是從衍生指標類別轉換成指標至基底類別。 另一個用途是要拋棄**const**性質的變數，以將它傳遞給需要非函式-**const**引數。 大部分的這些型別轉換作業會有一些風險。

在 c-style 程式設計中，相同的 c-style 轉換運算子用於所有類型的轉換 （cast）。

```cpp
(int) x; // old-style cast, old-style syntax
int(x); // old-style cast, functional syntax
```

C 樣式轉型運算子等同於呼叫運算子 （），因此不起眼在程式碼和容易被忽略。 兩者都是不正確的因為難以辨識在瀏覽或搜尋，而且它們夠不同，無法叫用的任何組合**靜態**， **const**，和**reinterpret_cast**. 找出使用舊式的轉換，否則實際上沒有可能既困難又容易發生錯誤。 基於這些理由，需要，轉型時，我們會建議使用下列 c + + 轉型的運算子在某些情況下明顯更多類型安全，而且更明確地快速程式設計目的的其中一個：

- **static_cast**，只會檢查在編譯的轉換時間。 **static_cast**會傳回錯誤，如果編譯器偵測到您嘗試不完全相容的類型之間進行轉換。 您也可以使用它以指標為基礎和指標衍生，之間進行轉換，但編譯器永遠無法辨識這類轉換是否會在執行階段的安全。

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

   如需詳細資訊，請參閱 < [static_cast](../cpp/static-cast-operator.md)。

- **dynamic_cast**，指標-基底指標衍生的安全、 執行階段檢查的轉換。 A **dynamic_cast**比安全**static_cast**向下轉型，但執行階段檢查時產生額外負荷。

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

   如需詳細資訊，請參閱 < [dynamic_cast](../cpp/dynamic-cast-operator.md)。

- **const_cast**，針對轉型**const**性質的變數，或轉換非-**const**變數**const**。 轉型**const**-使用此運算子的性質是只為出錯因為使用 c-style 轉型，差別在於使用**const 轉換**就比較不容易不小心執行轉換。 有時候您必須能**const**-性質的變數，例如，傳遞**const**函式採用非變數**const**參數。 下列範例顯示如何執行這項工作。

    ```cpp
    void Func(double& d) { ... }
    void ConstCast()
    {
       const double pi = 3.14;
       Func(const_cast<double&>(pi)); //No error.
    }
    ```

   如需詳細資訊，請參閱 < [const_cast](../cpp/const-cast-operator.md)。

- **reinterpret_cast**，針對之間的轉換 （cast） 這類不相關型別**指標**要**int**。

    > [!NOTE]
    >  視其他經常不使用此轉換運算子，它具有不保證可以移植到其他編譯器。

   下列範例說明如何**reinterpret_cast**有別**static_cast**。

    ```cpp
    const char* str = "hello";
    int i = static_cast<int>(str);//error C2440: 'static_cast' : cannot
                                  // convert from 'const char *' to 'int'
    int j = (int)str; // C-style cast. Did the programmer really intend
                      // to do this?
    int k = reinterpret_cast<int>(str);// Programming intent is clear.
                                       // However, it is not 64-bit safe.
    ```

   如需詳細資訊，請參閱 < [reinterpret_cast 運算子](../cpp/reinterpret-cast-operator.md)。

## <a name="see-also"></a>另請參閱

[C + + 類型系統](../cpp/cpp-type-system-modern-cpp.md)<br/>
[歡迎回到 C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)