---
title: 來源的程式碼組織 （c + + 範本） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 50569c5d-0219-4966-9bcf-a8689074ad1d
author: mikeblome
ms.author: mblome
ms.openlocfilehash: ef23b1a12305be9ecf181beb085bb686e81b083b
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939750"
---
# <a name="source-code-organization-c-templates"></a>原始程式碼組織 （c + + 樣板）

在定義類別樣板，您必須組織的方式需要它們時，會顯示給編譯器的成員定義中的原始程式碼。   您可以選擇使用*包含模型*或*明確具現化*模型。 在包含模型中，您可以包含在使用範本的每個檔案中的成員定義。 這種方法是最簡單的並提供最大的彈性，以具象類型可以搭配您的範本。 其缺點是，它可能會增加編譯時間。 影響可能很大，如果專案和/或包含的檔案本身很大。 使用明確具現化方法時，範本本身執行個體化具象類別或特定類型的類別成員。  這種方法可以加快編譯時間，但它會限制要事先啟用範本實作這些類別的使用方式。 一般情況下，我們建議您除非編譯時間會變成問題時，才使用包含模型。

## <a name="background"></a>背景

為範本，因為編譯器不會產生範本，或其任何成員的物件程式碼的一般類別一樣。 沒有要產生之前的具象類型具現化的範本。 當編譯器遇到樣板具現化這類`MyClass<int> mc;`並沒有具有該簽章的類別存在，它會產生新的類別。 它也會嘗試產生任何成員函式中所使用的程式碼。 這些定義是否在檔案不是 #included，直接或間接地在.cpp 檔案中已編譯，編譯器不會察覺就是了。  從編譯器的觀點來看，這不一定是錯誤因為函式可能在另一個轉譯單位中，案例，連結器會尋找這些定義。  如果連結器找不到該程式碼，則會引發**無法解析的外部**時發生錯誤。

## <a name="the-inclusion-model"></a>包含模型

若要在整個轉譯單位中，顯示樣板定義的最簡單且最常見的方式是放在標頭檔本身的定義。  使用範本的任何.cpp 檔只需要 #include 標頭。 這是標準程式庫中使用的方法。

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

使用此方法時，編譯器會有完整的範本定義之存取權，並可以具現化範本隨任何型別。 它是簡單且相對較容易維護。 不過，包含模型沒有編譯時間方面的成本。   這項成本可能很大，在大型程式中，特別是當範本標頭本身 #includes 其他標頭。 每個.cpp 檔案的 #includes 標頭會收到它自己的函式樣板和所有定義的複本。 連結器通常可以周旋，讓您執行不得到多個定義的函式，但花時間進行這項工作。 額外編譯時間可能不是明顯較小的程式。

## <a name="the-explicit-instantiation-model"></a>明確具現化模型

如果包含模型項目並不可行，為您的專案，而且您明確知道將用來具現化樣板的型別，然後您可以區隔的.h 和.cpp 檔案，將範本程式碼而在.cpp 檔案中明確樣板具現化。 這會導致物件要產生的程式碼，編譯器將會看到當它遇到使用者具現化。

您可以使用後面接著您要具現化之實體的簽章的關鍵字範本建立的明確具現化。 這可以是類型或成員。 如果您明確具現化類型，所有成員會具現都化。

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
#include "stdafx.h"
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

在上述範例中，明確具現化是在.cpp 檔案的底部。 A`MyArray`僅適用於可能**double**或`String`型別。

> [!NOTE]
> 在 c++11**匯出**關鍵字已被取代的範本定義內容中。 實際上這會有太大的影響，因為大多數的編譯器永遠不會支援它。
