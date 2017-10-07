---
title: "命名空間 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 08/30/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- namespace_CPP
dev_langs:
- C++
helpviewer_keywords:
- namespaces [C++], C++
- namespaces [C++]
- namespaces [C++], global
- global namespace
- Visual C++, namespaces
ms.assetid: d1a5a9ab-1cad-47e6-a82d-385bb77f4188
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: deb5926f15e4efad4378a9930f1e353e9af58516
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="namespaces-c"></a>命名空間 (C++)
命名空間是提供其內識別項 (類型、函式、變數等的名稱) 範圍的宣告式區域。 命名空間用來將程式碼組織成邏輯群組，以及防止特別在程式碼基底包含多個程式庫時可能會發生的名稱衝突。 在命名空間範圍的所有識別項都可以看得到彼此，沒有限制。 命名空間外部的識別項可以使用完整的名稱，每個識別項，例如存取成員`std::vector<std::string> vec;`，或藉由[using 宣告](../cpp/using-declaration.md)單一識別項 (`using std::string`)，或[using 指示詞](../cpp/namespaces-cpp.md#using_directives)針對命名空間中的所有識別項 (`using namespace std;`)。 標頭檔中的程式碼應該一律使用完整命名空間名稱。  
  
 下列範例顯示一個命名空間宣告，以及命名空間外部的程式碼可以存取其成員的三種方式。  
  
```cpp  
namespace ContosoData  
{      
    class ObjectManager   
    {  
    public:  
        void DoSomething() {}  
    };  
    void Func(ObjectManager) {}  
}  
```  
  
 使用完整名稱：  
  
```cpp  
ContosoData::ObjectManager mgr;  
mgr.DoSomething();  
ContosoData::Func(mgr);  
```  
  
 使用 using 宣告，將一個識別項帶入範圍中：  
  
```cpp  
using ContosoData::ObjectManager;  
ObjectManager mgr;  
mgr.DoSomething();  
  
```  
  
 使用 using 指示詞，將命名空間中的所有項目帶入範圍中：  
  
```cpp  
using namespace ContosoData;
  
ObjectManager mgr;  
mgr.DoSomething();  
Func(mgr);  
  
```  
  
## <a id="using_directives"></a>using 指示詞  
 `using`指示詞可讓中的所有名稱**命名空間**沒有*命名空間名稱*做為明確限定詞。 使用 using 指示詞在實作檔 (也就是 *.cpp) 如果您使用數個不同的識別項中的命名空間。如果您只使用一個或兩個識別項，然後考慮使用 using 宣告只這些識別項帶入範圍並不是所有的識別項命名空間中。 如果區域變數的名稱和命名空間變數相同，命名空間變數將會隱藏。 命名空間變數的名稱與全域變數名稱相同，會產生錯誤。  
  
> [!NOTE]
>  using 指示詞可以放在 .cpp 檔案頂端 (在檔案範圍中) 或是類別或函式定義內。  
>   
>  一般而言，請避免將 using 指示詞放在標頭檔 (*.h) 中，因為包含該標頭的所有檔案都會將命名空間中的所有項目帶入範圍中，這樣會導致很難偵錯的名稱隱藏和命名衝突問題。 請一律在標頭檔中使用完整名稱。 如果這些名稱太長，您可以使用命名空間別名來縮短它們。 (請參閱下方。)  
  
## <a name="declaring-namespaces-and-namespace-members"></a>宣告命名空間和命名空間成員  
 一般而言，您可以在標頭檔中宣告命名空間。 如果函式實作位於個別的檔案，則請限定函式名稱 (如此範例所示)。  
  
```cpp  
//contosoData.h   
#pragma once  
namespace ContosoDataServer  
{  
    void Foo();  
    int Bar();  
  
}  
```  
  
 即使您放置在 contosodata.cpp 函式實作應該使用完整限定的名稱，`using`指示詞檔案的頂端：  
  
```cpp  
#include "contosodata.h"  
using namespace ContosoDataServer;   
  
void ContosoDataServer::Foo() // use fully-qualified name here  
{  
   // no qualification needed for Bar()  
   Bar();   
}  
  
int ContosoDataServer::Bar(){return 0;}  
```  
  
 命名空間可以宣告在單一檔案的多個區塊中以及多個檔案中。 編譯器會在前置處理期間將組件加在一起，而產生的命名空間包含所有組件中宣告的所有成員。 其中一個範例是標準程式庫之每個標頭檔中所宣告的 std 命名空間。  
  
 具名命名空間的成員可以明確定義的名稱限定所宣告的命名空間外部定義。 不過，定義必須出現在命名空間中含括宣告之命名空間的宣告位置後面。 例如:  
  
```cpp  
// defining_namespace_members.cpp  
// C2039 expected  
namespace V {  
        void f();  
    }  
  
    void V::f() { }        // ok  
    void V::g() { }        // C2039, g() is not yet a member of V  
  
    namespace V {  
        void g();  
    }  
}  
```  
  
 如果跨多個標頭檔宣告命名空間成員，而且您尚未以正確的順序包括這些標頭，則會發生此錯誤。  
  
## <a name="the-global-namespace"></a>全域命名空間  
 如果明確命名空間中未宣告識別項，則它是隱含全域命名空間的一部分。 一般情況下，嘗試避免進行宣告，在全域範圍，如果可能的話，除了的進入點[main 函式](../c-language/main-function-and-program-execution.md)，所需全域命名空間中。 若要明確限定全域識別項，請使用沒有名稱的範圍解析運算子 (如在 `::SomeFunction(x);` 中)。 這會區分識別項與任何其他命名空間中具有相同名稱的任何項目，也有助於讓其他人容易了解您的程式碼。  
  
## <a name="the-std-namespace"></a>std 命名空間  
 所有 c + + 標準程式庫類型和函式中宣告`std`命名空間或命名空間巢狀方式置於`std`。  
  
## <a name="nested-namespaces"></a>巢狀命名空間  
 命名空間可能是巢狀命名空間。 一般巢狀命名空間具有其父成員的不合格存取，但父成員沒有巢狀命名空間的不合格存取 (除非它被宣告為內嵌) (如下列範例所示)：  
  
```cpp  
namespace ContosoDataServer  
{  
    void Foo();   
  
    namespace Details  
    {  
        int CountImpl;  
        void Ban() { return Foo(); }  
    }  
  
    int Bar(){...};  
    int Baz(int i) { return Details::CountImpl; }      
  
}  
```  
  
 一般巢狀命名空間可以用來封裝不屬於父命名空間之公用介面的內部實作詳細資料。  
  
## <a name="inline-namespaces-c-11"></a>內嵌命名空間 (C++ 11)  
 相較於一般巢狀命名空間，內嵌命名空間成員是視為父命名空間的成員。 這種特性會啟用多載函式上的引數相依查閱，以處理父命名空間和巢狀內嵌命名空間中具有多載的函式。 它也可讓您宣告在內嵌命名空間中所宣告樣板之父命名空間中的特製化。 下列範例示範外部程式碼預設如何繫結到內嵌命名空間：  
  
```cpp  
//Header.h  
#include <string>  
  
namespace Test  
{  
    namespace old_ns  
    {  
        std::string Func() { return std::string("Hello from old"); }  
    }  
  
    inline namespace new_ns  
    {  
        std::string Func() { return std::string("Hello from new"); }  
    }  
}  
  
#include "header.h"  
#include <string>  
#include <iostream>  
  
int main()  
{  
    using namespace Test;  
    using namespace std;  
  
    string s = Func();  
    std::cout << s << std::endl; // "Hello from new"  
    return 0;  
}  
```  
  
 下列範例示範如何在內嵌命名空間中所宣告樣板之父系中的特製化。  
  
```cpp  
namespace Parent  
{  
    inline namespace new_ns  
    {  
         template <typename T>  
         struct C  
         {  
             T member;  
         };  
    }  
     template<>  
     class C<int> {};  
}  
  
```  
  
 您可以使用內嵌命名空間做為版本設定機制，來管理程式庫的公用介面變更。 例如，您可以建立單一父命名空間，並封裝父命名空間內其專屬巢狀命名空間中的每個介面版本。 保留最新或慣用版本的命名空間限定為內嵌，因此予以公開，就像它是父命名空間的直接成員一樣。 叫用 Parent::Class 的用戶端程式碼將會自動繫結至新的程式碼。 偏好使用舊版本的用戶端還是可以使用具有該程式碼之巢狀命名空間的完整路徑來存取它。  
  
 內嵌關鍵字必須套用至編譯單位中命名空間的第一個宣告。  
  
 下列範例示範介面的兩個版本，各位於巢狀命名空間中。 `v_20` 命名空間具有 `v_10` 介面的某個修改，並標示為內嵌。 使用新程式庫並呼叫 `Contoso::Funcs::Add` 的用戶端程式碼將會叫用 v_20 版本。 嘗試呼叫 `Contoso::Funcs::Divide` 的程式碼現在會產生編譯時期錯誤。 如果它們真正需要該函式，則仍然可以透過明確呼叫 `Contoso::v_10::Funcs::Divide` 來存取 `v_10` 版本。  
  
```cpp  
namespace Contoso  
{  
    namespace v_10  
    {  
        template <typename T>  
        class Funcs  
        {  
        public:  
            Funcs(void);  
            T Add(T a, T b);  
            T Subtract(T a, T b);  
            T Multiply(T a, T b);  
            T Divide(T a, T b);  
        };  
    }  
  
    inline namespace v_20  
    {  
        template <typename T>  
        class Funcs  
        {  
        public:  
            Funcs(void);  
            T Add(T a, T b);  
            T Subtract(T a, T b);  
            T Multiply(T a, T b);  
            std::vector<double> Log(double);  
            T Accumulate(std::vector<T> nums);  
      };  
    }  
}  
  
```  
  
## <a id="namespace_aliases"></a>命名空間別名  
 命名空間名稱必須是唯一的，這表示通常應該不會太短。 如果名稱長度導致難以讀取程式碼，或在不能使用 using 指示詞的標頭檔中所輸入的名稱長度過於冗長，則可以建立命名空間別名做為實際名稱的縮寫。 例如:  
  
```cpp  
namespace a_very_long_namespace_name { class Foo {}; }  
namespace AVLNN = a_very_long_namespace_name;  
void Bar(AVLNN::Foo foo){ }  
  
```  
  
## <a name="anonymous-or-unnamed-namespaces"></a>匿名或未命名的命名空間  
 您可以建立明確命名空間，而不是指定它的名稱：  
  
```cpp  
namespace  
{  
    int MyFunc(){}  
}  
```  
  
 這稱為未命名或匿名命名空間，而且您想要讓其他檔案中的變數宣告看不到程式碼時很有用 （也就是提供其內部連結） 而不需要建立具名命名空間。 相同檔案中的所有程式碼都可以看到未命名的命名空間中的識別項，但在該檔案外部 (或更精確地來說是外部轉譯單位) 看不到識別碼以及命名空間本身。  
  
## <a name="see-also"></a>另請參閱  
 [宣告和定義](declarations-and-definitions-cpp.md)

