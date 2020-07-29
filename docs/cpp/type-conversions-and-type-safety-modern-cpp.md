---
title: 類型轉換與類型安全
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 629b361a-2ce1-4700-8b5d-ab4f57b245d5
ms.openlocfilehash: 28adbc261b5b4376f947e00695fe66650739438d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223534"
---
# <a name="type-conversions-and-type-safety"></a>類型轉換與類型安全

本檔會識別常見的類型轉換問題，並說明如何在您的 c + + 程式碼中加以避免。

當您撰寫 c + + 程式時，請務必確定它是型別安全的。 這表示每個變數、函式引數和函式傳回值都是儲存可接受的資料類型，而涉及不同類型值的作業則不會造成資料遺失、不正確的位模式解讀或記憶體損毀。 永遠不會明確或隱含地將值從一個類型轉換成另一個類型的程式，是由定義的型別安全。 不過，有時候也需要類型轉換，甚至是不安全的轉換。 例如，您可能必須將浮點運算的結果儲存在類型的變數中 **`int`** ，或者您可能必須將中的值傳遞 **`unsigned int`** 至接受的函式 **`signed int`** 。 這兩個範例都會說明不安全的轉換，因為它們可能會導致資料遺失或重新轉譯值。

當編譯器偵測到不安全的轉換時，會發出錯誤或警告。 錯誤停止編譯;警告可讓編譯繼續進行，但在程式碼中表示可能發生的錯誤。 不過，即使您的程式編譯時不會出現警告，仍然可能包含會導致隱含類型轉換產生不正確結果的程式碼。 類型錯誤也可以透過程式碼中的明確轉換或轉換來引入。

## <a name="implicit-type-conversions"></a>隱含類型轉換

當運算式包含不同內建類型的運算元，而且沒有明確轉換時，編譯器會使用內建的*標準轉換*來轉換其中一個運算元，讓類型相符。 編譯器會以定義完善的順序來嘗試轉換，直到其中一個成功為止。 如果選取的轉換是升級，則編譯器不會發出警告。 如果轉換為縮小，則編譯器會發出有關可能遺失資料的警告。 實際資料遺失的發生與否取決於相關的實際值，但我們建議您將此警告視為錯誤。 如果涉及使用者定義型別，則編譯器會嘗試使用您在類別定義中所指定的轉換。 如果找不到可接受的轉換，則編譯器會發出錯誤，而且不會編譯器。 如需有關管理標準轉換之規則的詳細資訊，請參閱[標準轉換](../cpp/standard-conversions.md)。 如需使用者定義轉換的詳細資訊，請參閱[使用者定義的轉換（c + +/cli）](../dotnet/user-defined-conversions-cpp-cli.md)。

### <a name="widening-conversions-promotion"></a>擴輾轉換（升級）

在擴輾轉換中，較小的變數中的值會指派給較大的變數，而不會遺失資料。 因為擴輾轉換一律是安全的，所以編譯器會以無訊息模式執行，而且不會發出警告。 下列轉換是擴輾轉換。

|寄件者|收件者|
|----------|--------|
|**`signed`** 或以外的任何或 **`unsigned`** 整數類型 **`long long`****`__int64`**|**`double`**|
|**`bool`** 或**`char`**|任何其他內建類型|
|**`short`** 或**`wchar_t`**|**`int`**, **`long`**, **`long long`**|
|**`int`**, **`long`**|**`long long`**|
|**`float`**|**`double`**|

### <a name="narrowing-conversions-coercion"></a>縮小轉換（強制型轉）

編譯器會以隱含方式執行縮小轉換，但會警告您可能遺失資料。 請務必認真地採取這些警告。 如果您確定不會發生任何資料遺失，因為較大的變數中的值一定會符合較小的變數，然後加入明確轉換，讓編譯器不會再發出警告。 如果您不確定轉換是安全的，請將某種執行時間檢查新增至程式碼，以處理可能的資料遺失，使其不會造成您的程式產生不正確的結果。

從浮點類型到整數類型的任何轉換都是縮小轉換，因為浮點值的小數部分會被捨棄並遺失。

下列程式碼範例顯示一些隱含的縮小轉換，以及編譯器針對它們發出的警告。

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

### <a name="signed---unsigned-conversions"></a>簽署不帶正負號的轉換

帶正負號的整數類資料類型和其不帶正負號的對應一律是相同的大小，但不同之處在于如何解讀值轉換的位模式。 下列程式碼範例示範當相同的位模式被視為帶正負號的值和不帶正負號的值時，會發生什麼事。 儲存在和中的位 `num` 模式 `num2` 永遠不會變更，如先前的圖例所示。

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

請注意，這兩個方向的值都是向量的。 如果您的程式產生奇怪的結果，其中值的正負號看起來與預期的相反，請尋找帶正負號和不帶正負號的整數類資料類型之間的隱含轉換。 在下列範例中，運算式（0-1）的結果會在 **`int`** **`unsigned int`** 儲存在中時，從隱含地轉換為 `num` 。 這會導致向量位模式。

```cpp
unsigned int u3 = 0 - 1;
cout << u3 << endl; // prints 4294967295
```

編譯器不會警告帶正負號和不帶正負號整數類資料類型之間的隱含轉換。 因此，我們建議您避免已登入不帶正負號的轉換。 如果您無法避免這些問題，請將執行時間檢查新增至您的程式碼，以偵測要轉換的值是否大於或等於零，而且小於或等於帶正負號類型的最大值。 此範圍中的值會從帶正負號的轉換成不帶正負號的，或從不帶正負號的未向量

### <a name="pointer-conversions"></a>指標轉換

在許多運算式中，C 樣式陣列會隱含地轉換成陣列中第一個專案的指標，而常數轉換則會以無訊息方式發生。 雖然這很方便，但也可能容易出錯。 例如，下列設計錯誤的程式碼範例看似無意義，但它會編譯並產生 ' p ' 的結果。 首先，"Help" 字串常值會轉換成，指向 **`char*`** 陣列的第一個元素; 該指標接著會由三個元素遞增，使其現在指向最後一個元素 ' p '。

```cpp
char* s = "Help" + 3;
```

## <a name="explicit-conversions-casts"></a>明確轉換（轉換）

藉由使用轉換作業，您可以指示編譯器將一種類型的值轉換成另一種類型。 在某些情況下，如果這兩個類型完全無關，編譯器會引發錯誤，但是在其他情況下，即使作業不是型別安全，也不會引發錯誤。 請謹慎使用轉換，因為從某種類型轉換成另一種是程式錯誤的潛在來源。 不過，有時候會需要轉換，而不是所有的轉換都有同樣的危險。 轉換的有效用法是當您的程式碼執行縮小轉換，而且您知道轉換不會造成您的程式產生不正確的結果。 實際上，這會告訴編譯器您知道您正在執行的作業，以及停止中斷您的相關警告。 另一個用法是將指標衍生類別轉換為指標對基底類別。 另一個用途是將變數的特性轉 **`const`** 型為不需要非引數的函式 **`const`** 。 大部分的轉換作業都牽涉到一些風險。

在 C 樣式程式設計中，會針對所有類型的轉換使用相同的 C 樣式轉型運算子。

```cpp
(int) x; // old-style cast, old-style syntax
int(x); // old-style cast, functional syntax
```

C 樣式轉換運算子等同于呼叫運算子（），因此會在程式碼中 inconspicuous 並容易忽略。 這兩者都是不好的，因為他們難以辨識或搜尋，而且兩者的不同之處在于叫用、和的任何組合 **`static`** **`const`** **`reinterpret_cast`** 。 找出原本的格式轉換實際上可能很棘手，而且容易出錯。 基於上述所有原因，當需要轉換時，建議您使用下列其中一種 c + + 轉型運算子，在某些情況下，它會有更多型別安全，並以更明確的方式表達程式設計意圖：

- **`static_cast`**，適用于在編譯時期檢查的轉換。 **`static_cast`** 如果編譯器偵測到您嘗試在完全不相容的類型之間進行轉換，則會傳回錯誤。 您也可以使用它，在指標對基底和指標衍生之間進行轉換，但編譯器不一定會在執行時間判斷這類轉換是否安全。

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

   如需詳細資訊，請參閱 [`static_cast`](../cpp/static-cast-operator.md)。

- **`dynamic_cast`**，針對安全的執行時間檢查，將指標轉型轉換成衍生的指標。 A **`dynamic_cast`** 比向下轉換更安全 **`static_cast`** ，但執行時間檢查會產生一些額外負荷。

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

   如需詳細資訊，請參閱 [`dynamic_cast`](../cpp/dynamic-cast-operator.md)。

- **`const_cast`**，用於轉型為 **`const`** 變數的性質，或 **`const`** 將非變數轉換為 **`const`** 。 藉 **`const`** 由使用這個運算子，就像使用 C 樣式的轉型一樣容易發生錯誤，不同之處在于 **`const_cast`** 您不可能不小心執行轉換。 有時候您必須轉換掉變數的 **`const`** 性質，例如，將 **`const`** 變數傳遞給採用非參數的函式 **`const`** 。 下列範例示範如何執行。

    ```cpp
    void Func(double& d) { ... }
    void ConstCast()
    {
       const double pi = 3.14;
       Func(const_cast<double&>(pi)); //No error.
    }
    ```

   如需詳細資訊，請參閱[const_cast](../cpp/const-cast-operator.md)。

- **`reinterpret_cast`**，用於不相關的類型（例如指標類型和）之間的轉換 **`int`** 。

    > [!NOTE]
    >  這個轉型運算子不常使用，而且不保證可移植到其他編譯器。

   下列範例說明如何 **`reinterpret_cast`** 與不同 **`static_cast`** 。

    ```cpp
    const char* str = "hello";
    int i = static_cast<int>(str);//error C2440: 'static_cast' : cannot
                                  // convert from 'const char *' to 'int'
    int j = (int)str; // C-style cast. Did the programmer really intend
                      // to do this?
    int k = reinterpret_cast<int>(str);// Programming intent is clear.
                                       // However, it is not 64-bit safe.
    ```

   如需詳細資訊，請參閱[ `reinterpret_cast` 運算子](../cpp/reinterpret-cast-operator.md)。

## <a name="see-also"></a>另請參閱

[C + + 類型系統](../cpp/cpp-type-system-modern-cpp.md)<br/>
[歡迎回到 c + +](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C + + 語言參考](../cpp/cpp-language-reference.md)<br/>
[C + + 標準程式庫](../standard-library/cpp-standard-library-reference.md)
