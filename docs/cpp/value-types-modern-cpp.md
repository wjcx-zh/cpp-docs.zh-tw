---
title: 實值類型 （現代 c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7e49c97bca86b8d2debde2f5b132f7dde16998e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32423414"
---
# <a name="value-types-modern-c"></a>實值類型 (現代 C++)
C + + 類別並不會預設實值類型。 本主題提供簡介性概觀的實值類型以及與其用途相關的問題。  
  
## <a name="value-vs-reference-types"></a>值與參考類型  
 如先前所述，c + + 類別會由預設實值類型。 他們可以指定為參考型別，可讓多型行為，以支援物件導向程式設計。 而參考類型的基底類別和虛擬函式相關對於多型的目的而言，實值型別有時檢視觀點的記憶體和版面配置控制項。 根據預設，實值類型是複製，這表示沒有一定的複製建構函式和複製指派運算子。 參考類型，您將類別變成不可複製 （停用複製建構函式和複製指派運算子），並使用虛擬解構函式，可支援其預期的多型。 實值類型也是這樣，它們會複製時，一律提供您兩個獨立的值可以修改個別的內容。 參考型別會識別為物件的類型為何，它的相關？ 基於這個理由，「 參考類型"也稱為 「 多型類型 」。  
  
 如果您真的想類似參考類型 （基底類別、 虛擬函式），您需要明確停用複製，如下所示`MyRefType`下列程式碼中的類別。  
  
```cpp  
// cl /EHsc /nologo /W4  
  
class MyRefType {  
private:  
    MyRefType & operator=(const MyRefType &);  
    MyRefType(const MyRefType &);  
public:  
    MyRefType () {}  
};  
  
int main()  
{  
    MyRefType Data1, Data2;  
    // ...  
    Data1 = Data2;  
}  
```  
  
 編譯上述程式碼會產生下列錯誤：  
  
```Output  
test.cpp(15) : error C2248: 'MyRefType::operator =' : cannot access private member declared in class 'MyRefType'  
        meow.cpp(5) : see declaration of 'MyRefType::operator ='  
        meow.cpp(3) : see declaration of 'MyRefType'  
  
```  
  
## <a name="value-types-and-move-efficiency"></a>實值類型，並移動效率  
 由於新的複本最佳化功能可以避免複製配置額外負荷。 比方說，當您插入向量的字串中間的字串時，會有任何複本重新配置額外負荷，只移動-即使則會導致向量本身的成長。 這也適用於其他作業，例如新增上執行運算的兩個非常大的物件。 如何啟用這些值的作業最佳化？ 在某些 c + + 編譯器，編譯器將會啟用此功能，您隱含方式一樣，編譯器可以自動產生複製建構函式。 不過，在 Visual c + + 中，您的類別必須為 「 選擇加入 「 移動指派和建構函式宣告在類別定義中。 這會透過使用雙連字號 (（& s) （& s)) 函式宣告和定義的移動建構函式和移動指派方法，將適當的成員中的右值參考。  您也需要插入正確的程式碼，從來源物件的 「 竊取內容 」。  
  
 如何決定是否您需要移動啟用？ 如果您已經知道您需要將複製建構已啟用，您可能想移動已啟用，如果成本比的深層複本。 不過，如果您知道您需要移動的支援，它不一定表示您想要啟用的複本。 後者的情況下會稱為 「 僅移動類型 」。 已經在標準程式庫中的範例是`unique_ptr`。 附帶一提，舊`auto_ptr`已被取代，並已被取代`unique_ptr`精確的前一版的 c + + 中的移動語意支援不足。  
  
 使用移動語意，您可以傳回值或插入在中間。 移動是複製的最佳方法。 沒有因應措施的堆積配置的需要。 請考慮下列虛擬程式碼：  
  
```cpp  
#include <set>  
#include <vector>  
#include <string>  
using namespace std;  
  
//...  
set<widget> LoadHugeData() {  
    set<widget> ret;  
    // ... load data from disk and populate ret  
    return ret;  
}  
//...  
widgets = LoadHugeData();   // efficient, no deep copy  
  
vector<string> v = IfIHadAMillionStrings();  
v.insert( begin(v)+v.size()/2, "scott" );   // efficient, no deep copy-shuffle  
v.insert( begin(v)+v.size()/2, "Andrei" );  // (just 1M ptr/len assignments)  
//...  
HugeMatrix operator+(const HugeMatrix& , const HugeMatrix& );  
HugeMatrix operator+(const HugeMatrix& ,       HugeMatrix&&);  
HugeMatrix operator+(      HugeMatrix&&, const HugeMatrix& );  
HugeMatrix operator+(      HugeMatrix&&,       HugeMatrix&&);  
//...  
hm5 = hm1+hm2+hm3+hm4+hm5;   // efficient, no extra copies  
```  
  
### <a name="enabling-move-for-appropriate-value-types"></a>啟用適當的實值類型的移動  
 值類似的類別，可以比的深層複本廉價移動，啟用移動建構和移動指派，以提升效率。 請考慮下列虛擬程式碼：  
  
```cpp  
#include <memory>  
#include <stdexcept>  
using namespace std;  
// ...  
class my_class {  
    unique_ptr<BigHugeData> data;  
public:  
    my_class( my_class&& other )   // move construction  
        : data( move( other.data ) ) { }  
    my_class& operator=( my_class&& other )   // move assignment  
    { data = move( other.data ); return *this; }  
    // ...  
    void method() {   // check (if appropriate)  
        if( !data )   
            throw std::runtime_error("RUNTIME ERROR: Insufficient resources!");  
    }  
};  
  
```  
  
 如果您啟用複製建構/指派時，也啟用移動建構/指派，如果可以成本比的深層複本。  
  
 某些*非值*類型是僅移動，例如當您無法複製的資源，只轉送擁有權。 範例：`unique_ptr`。  
  
## <a name="section"></a>區段  
 內容  
  
## <a name="see-also"></a>另請參閱  
 [C + + 類型系統](../cpp/cpp-type-system-modern-cpp.md)   
 [歡迎回到 c + +](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)