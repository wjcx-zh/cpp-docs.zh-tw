---
title: "來源的程式碼的組織 （c + + 範本） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 50569c5d-0219-4966-9bcf-a8689074ad1d
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: 1b3b17c17bad3834774f747548dda6710e178cb4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="source-code-organization-c-templates"></a>來源的程式碼組織 （c + + 樣板）

在定義類別樣板時，您必須組織的方式需要它們時，會顯示編譯器的成員定義中的原始程式碼。   您可以選擇使用*包含模型*或*明確具現化*模型。 在包含模型中，您可以包括使用範本的每個檔案中的成員定義。 此方法是最簡單的並提供最大彈性的具象類型可以搭配您的範本。 其缺點是它可能會增加編譯時間。 影響可能會很顯著，如果專案和/或被納入的檔案本身很大。 使用明確具現化方法時，實體類別或類別成員的特定類型，具現化範本本身。  這種方法可以加快編譯時間，但它會限制範本實作者事先啟用這些類別的使用方式。 一般情況下，我們建議您除非編譯時間會變成問題時，才使用包含模型。  
  
## <a name="background"></a>背景

 範本不是一般類別，因為編譯器不會產生物件程式碼的範本，或它的任何成員一樣。 沒有要產生具象型別與具現化樣板之前項目。 當編譯器遇到樣板具現化例如`MyClass<int> mc;`及還沒有任何使用該簽章的類別，會產生新的類別。 它也會嘗試產生其程式碼所使用的任何成員函式。 如果這些定義是不是檔案中 #included，直接或間接地在.cpp 檔案中編譯，編譯器無法看到它們。  從編譯器的觀點來看，這不一定是錯誤因為函式可能在另一個轉譯單位中，大小寫連結器會發現這些定義。  如果連結器找不到該程式碼，則會引發**未解析的外部**錯誤。  

## <a name="the-inclusion-model"></a>包含模型

 要顯示在轉譯單位中，範本定義的最簡單且最常見方式是將定義放在標頭檔本身。  只要有任何使用範本的.cpp 檔案 #include 的標頭。 這是標準程式庫中使用的方法。  
  
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
  
 使用此方法時，編譯器會有完整的範本定義之存取權，並可以具現化範本隨任何類型。 它是簡單且相對較容易維護。 不過，包含模型沒有成本編譯時間。   這個成本可能很大的程式，特別是本身的範本標頭 #includes 其他標頭。 每個.cpp 檔案的 #includes 標頭會取得自己的函式樣板，所有定義的複本。 連結器通常可以找出的項目，讓您不最後的多個定義的函式，但花時間來執行這項工作。 額外的編譯時間可能不是明顯較小的程式。  
  
## <a name="the-explicit-instantiation-model"></a>明確具現化模型

 如果包含模型並不可行，為您的專案，而且您知道針對將用來具現化樣板的型別，可以區隔至.h 和.cpp 檔案，將範本程式碼，即可在.cpp 檔案中明確具現化的範本。 這會導致產生物件程式碼，編譯器將會看到當它遇到使用者具現化。  
  
 您可以使用關鍵字範本，後面接著您想要具現化的實體的簽章建立明確具現化。 這可以是類型或成員。 如果您明確具現化類型，所有成員會具現都化。  
  
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
  
 在上述範例中，明確具現化是.cpp 檔案的底部。 A`MyArray`僅適用於可能**double**或**字串**型別。  
  
> [!NOTE]
>  C + + 11**匯出**關鍵字已被取代的範本定義的內容中。 實際上這有影響不大，因為大多數的編譯器永遠不會支援它。
