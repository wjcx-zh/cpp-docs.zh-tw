---
title: "明確預設和已刪除函數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: 5a588478-fda2-4b3f-a279-db3967f5e07e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 73e1d52d1c13e2defa51a5cab9da625b75aac757
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="explicitly-defaulted-and-deleted-functions"></a>明確的預設和被刪除的函式
在 C++11 中，預設和已刪除的函式可讓您明確控制是否要自動產生特殊成員函式。 被刪除的函式也提供您簡單語言，防止在所有類型函式 (特殊成員函式，一般成員函式和非成員函式) 的引數中發生有問題的類型提升 (原本可能會導致不必要的函式呼叫)。  
  
## <a name="benefits-of-explicitly-defaulted-and-deleted-functions"></a>明確預設和已刪除的函式的優點  
 在 C++ 中，如果類型未自動宣告，編譯器會自動產生預設建構函式、複製建構函式、複製指派運算子和解構函式。 這些函式稱為*特殊成員函式*，及它們可讓簡單使用者定義型別在 c + + 行為與 c 中的結構相同也就是說，您可以建立、 複製和終結它們，而不需要任何額外的程式碼撰寫工作。 C++11 語言引進移動語意，在編譯器可以自動產生的特殊成員函式清單中，加入移動建構函式和移動指派運算子。  
  
 這對簡單類型而言十分方便，但是複雜類型通常會自行定義一個或多個特殊成員函式，而且這可以防止自動產生其他特殊成員函式。 實際上：  
  
-   如果明確宣告任何建構函式，則不會自動產生任何預設建構函式。  
  
-   如果明確宣告虛擬解構函式，則不會自動產生任何預設解構函式。  
  
-   如果已明確宣告移動建構函式或移動指派運算子：  
  
    -   不會自動產生複製建構函式。  
  
    -   不會自動產生複製指派運算子。  
  
-   如果已明確宣告複製建構函式、複製指派運算子、移動建構函式、移動指派運算子或解構函式：  
  
    -   不會自動產生移動建構函式。  
  
    -   不會自動產生移動指派運算子。  
  
> [!NOTE]
>  此外，C++11 標準指定下列額外規則：  
>   
>  -   如果已明確宣告複製建構函式或解構函式，則複製指派運算子自動產生為已被取代。  
> -   如果已明確宣告複製指派運算子或解構函式，則複製建構函式自動產生為已被取代。  
>   
>  在這兩種情況下，Visual Studio 會繼續自動隱含產生必要函式，且不會發出警告。  
  
 這些規則的結果也可能滲入物件階層架構中。 例如，如果基底類別因故無法取得衍生類別可呼叫的預設建構函式 (也就是不接受任何參數的 `public` 或 `protected` 建構函式)，則從它衍生的類別無法自動產生自己的預設建構函式。  
  
 這些規則會讓應該簡單的實作、使用者定義類型和一般 C++ 慣用語更加複雜；例如，私下宣告複製建構函式和複製指派運算子，但未進行定義，以將使用者定義類型設定為不可複製。  
  
```  
struct noncopyable  
{  
  noncopyable() {};  
  
private:  
  noncopyable(const noncopyable&);  
  noncopyable& operator=(const noncopyable&);  
};  
```  
  
 在 C++11 之前，此程式碼片段是不可複製類型的慣用語表單。 不過，它有數個問題：  
  
-   必須私下宣告複製建構函式以將其隱藏，但是，因為它已完全進行宣告，所以無法自動產生預設建構函式。 如果您需要預設建構函式，則必須明確地定義預設建構函式，即使它不執行任何動作也是一樣。  
  
-   即使明確定義的預設建構函式不執行任何動作，編譯器還是會將它視為非一般。 其效率比自動產生的預設建構函式還要低，而且會防止 `noncopyable` 變成真正的 POD 類型。  
  
-   即使外部程式碼看不見複製建構函式和複製指派運算子，`noncopyable` 的成員函式和 friend 仍可以看見及呼叫它們。 如果宣告但未定義它們，則呼叫它們會導致連結器錯誤。  
  
-   雖然這是普遍接受的慣用語，但是用意不清楚，除非您了解自動產生特殊成員函式的所有規則。  
  
 在 C++11 中，non-copyable 慣用語可以用更直接的方式來實作。  
  
```  
struct noncopyable  
{  
  noncopyable() =default;  
  noncopyable(const noncopyable&) =delete;  
  noncopyable& operator=(const noncopyable&) =delete;  
};  
```  
  
 請注意如何解決 C++11 之前的慣用語問題：  
  
-   預設建構函式的產生仍是透過宣告複製建構函式加以避免，但是您可以明確預設以再次產生預設建構函式。  
  
-   明確預設的特殊成員函式仍視為一般，因此不會對效能造成負面影響，而且不會防止 `noncopyable` 成為真正的 POD 類型。  
  
-   複製建構函式和複製指派運算子是公用的，但已遭刪除。 它是定義或呼叫已刪除函式的編譯時期錯誤。  
  
-   意圖對所有了解 `=default` 和 `=delete` 的人來說很清楚。 您不需要了解自動產生特殊成員函式的規則。  
  
 具有類似的慣用語，可產生不可移動、只能動態配置或無法動態配置的使用者定義類型。 所有這些慣用語都有 C++11 之前的實作，而這些實作發生類似的問題，而且同樣可在 C++11 中獲得解決，方法是根據預設和已刪除的特殊成員函式來實作它們。  
  
## <a name="explicitly-defaulted-functions"></a>明確預設函式  
 您可以預設任何特殊成員函式：明確陳述特殊成員函式使用預設實作、定義具有非公用存取限定詞的特殊成員函式，或復原在其他情況下無法自動產生的特殊成員函式。  
  
 透過宣告，即可預設特殊成員函式宣告 (如此範例所示)：  
  
```  
struct widget  
{  
  widget()=default;  
  
  inline widget& operator=(const widget&);  
};  
  
inline widget& widget::operator=(const widget&) =default;  
```  
  
 請注意，只要特殊成員函式是可內嵌的，您就可以在類別主體外部預設特殊成員函式。  
  
 因為一般特殊成員函式的效能優勢，建議您在想要預設行為時偏好使用透過空白函式主體自動產生的特殊成員函式。 做法是明確預設特殊成員函式，或不予宣告 (也不宣告會防止自動產生它的其他特殊成員函式)。  
  
## <a name="deleted-functions"></a>已刪除的函式  
 您可以刪除特殊成員函式以及一般成員函式和非成員函式，以防止定義或呼叫它們。 刪除特殊成員函式，提供更簡潔的方法來防止編譯器產生您不想要的特殊成員函式。 函式必須在宣告時被刪除；不能透過可以先宣告再預設函式的方式之後刪除。  
  
```  
struct widget  
{  
  // deleted operator new prevents widget from being dynamically allocated.  
  void* operator new(std::size_t) = delete;  
};  
```  
  
 刪除一般成員函式或非成員函式，可防止有問題的類型提升呼叫非預期的函式。 這種方式適用，因為已刪除的函式仍參與多載解析，而且提供的相符程度高於提升類型之後可呼叫的函式。 函式呼叫解析為更特定、但已刪除的函式，且造成編譯器錯誤。  
  
```  
// deleted overload prevents call through type promotion of float to double from succeeding.  
void call_with_true_double_only(float) =delete;  
void call_with_true_double_only(double param) { return; }  
```  
  
 請注意，在上述範例中，使用 `call_with_true_double_only` 引數呼叫 `float` 會造成編譯器錯誤，但如果使用 `call_with_true_double_only` 引數呼叫 `int` 卻不會導致問題。在 `int` 案例中，引數會從 `int` 提升為 `double` 並成功呼叫 `double` 版本的函式，即使這不是一開始的目的。 若要確定使用 non-double 引數呼叫這個函式會造成編譯器錯誤，您可以宣告被刪除的函式的範本版本。  
  
```  
template < typename T >  
void call_with_true_double_only(T) =delete; //prevent call through type promotion of any T to double from succeeding.  
  
void call_with_true_double_only(double param) { return; } // also define for const double, double&, etc. as needed.  
  
```