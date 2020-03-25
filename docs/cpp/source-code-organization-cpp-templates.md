---
title: 原始程式碼組織 (C++ 範本)
ms.date: 04/22/2019
ms.assetid: 50569c5d-0219-4966-9bcf-a8689074ad1d
ms.openlocfilehash: 76898d04e5f9f0576898eb40945b7718c650d71a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178726"
---
# <a name="source-code-organization-c-templates"></a>原始程式碼組織 (C++ 範本)

定義類別範本時，您必須以這種方式組織原始程式碼，在需要時將成員定義顯示給編譯器。   您可以選擇使用「包含模型」或「明確具現化」模型。 在包含模型中，您可以在每個使用範本的檔案中包含成員定義。 此方法最簡單，且在可以使用範本的實體類別方面提供最大彈性。 其缺點是可能會增加編譯時間。 如果專案和/或 包含的檔案本身很大，則影響可能會很大。 使用明確具現化方法時，範本本身會具現化特定類型的實體類別或類別成員。  這種方法可以加快編譯時間，但僅限於範本實作者事先啟用之類別的使用方式。 除非編譯時間會造成問題，否則在一般情況下我們建議您使用包含模型。

## <a name="background"></a>背景

以編譯器不為範本或其任何成員產生物件程式碼的意義來說，範本與一般類別不同。 在使用實體類別將範本具現化之前，不會產生任何內容。 當編譯器遇到範本具現化 (例如 `MyClass<int> mc;`) 且不存在具有該簽章的類別時，將產生新的類別。 也會嘗試為所使用的任何成員函式產生程式碼。 如果這些定義位於不直接或間接包含於正在編譯的 .cpp 檔案中，則編譯器將無法看到這些定義。  從編譯器的觀點來看這不一定是錯誤，因為函式可能會在另一個轉譯單位中定義，在此情況下連結器會找到這些函式。  如果連結器找不到該程式碼，則會引發**無法解析的外部**錯誤。

## <a name="the-inclusion-model"></a>包含模型

在整個轉譯單位中顯示範本定義的最簡單和最常用方法是將定義放在標頭檔案中。  任何使用範本的任何 .cpp 檔案都必須包含標頭。 這是標準程式庫中使用的方法。

```cpp
#ifndef MYARRAY
#define MYARRAY
#include <iostream>

template<typename T, size_t N>
class MyArray
{
    T arr[N];
public:
    // Full definitions:
    MyArray(){}
    void Print()
    {
        for (const auto v : arr)
        {
            std::cout << v << " , ";
        }
    }

    T& operator[](int i)
   {
       return arr[i];
   }
};
#endif
```

透過此方法，編譯器可以存取完整的範本定義，並可以隨需針對任何類型將範本具現化。 此方法簡單且相對較容易維護。 不過，包含模型具有編譯時間方面的成本。   在大型程式中，這項成本可能很大，特別是當範本標頭本身包含其他標頭時。 包含標頭的每個 .cpp 檔案都會收到自己的函式範本複本和所有定義。 連結器通常能夠妥善處理，使您不至於面對函式具有多個定義的情況，但完成此工作需要時間。 在較小型的程式中，可能只需較短的額外編譯時間。

## <a name="the-explicit-instantiation-model"></a>明確具現化模型

如果包含模型對您的專案來說並不可行，且您清楚知道要用來將範本具現化的類型集，那麼您可以將範本程式碼區隔為 .h 和 .cpp 檔案，並在 .cpp 檔案中將範本明確具現化。 這會導致產生當編譯器遇到使用者具現化將會看到的物件程式碼。

您可以使用關鍵字範本，後面接著要具現化之實體的簽章，來建立明確具現化。 可以是類型或成員。 如果您將類型明確具現化，則所有成員會具現都化。

```cpp
template MyArray<double, 5>;
```

```cpp
//MyArray.h
#ifndef MYARRAY
#define MYARRAY

template<typename T, size_t N>
class MyArray
{
    T arr[N];
public:
    MyArray();
    void Print();
    T& operator[](int i);
};
#endif

//MyArray.cpp
#include <iostream>
#include "MyArray.h"

using namespace std;

template<typename T, size_t N>
MyArray<T,N>::MyArray(){}

template<typename T, size_t N>
void MyArray<T,N>::Print()
{
    for(const auto v : arr)
    {
        cout << v << "'";
    }
    cout << endl;
}

template MyArray<double, 5>;template MyArray<string, 5>;
```

在上述範例中，明確具現化是在 .cpp 檔案的底部。 `MyArray` 僅適用於 **double** 或 `String` 類型。

> [!NOTE]
> 在 C++11 中，**匯出**關鍵字已在範本定義的內容中淘汰。 實際上這不會有太大的影響，因為大多數的編譯器都未對其提供支援。
