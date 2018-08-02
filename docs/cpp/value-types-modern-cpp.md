---
title: 實值型別 （現代 c + +） |Microsoft Docs
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
ms.openlocfilehash: 3e7fb326b5a61daec2f3dcd78982694edb276323
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463125"
---
# <a name="value-types-modern-c"></a>實值類型 (現代 C++)
C + + 類別是由預設實值型別。 本主題提供概觀介紹的實值型別以及與其用途相關的問題。  
  
## <a name="value-vs-reference-types"></a>值與參考型別  
 如先前所述，c + + 類別會由預設實值型別。 他們可以指定為參考型別，可讓多型行為，可支援物件導向程式設計。 實值型別有時檢視觀點的記憶體和版面配置控制項，而參考型別是基底類別及虛擬函式的多型的目的。 根據預設，實值型別是複製，這表示總是有複製建構函式和複製指派運算子。 若是參考類型，您使類別不可複製 （停用複製建構函式和複製指派運算子），並使用虛擬解構函式，可支援其預期的多型。 實值型別也是這樣，進行複製時一律提供您兩個獨立的值，可以個別修改內容的相關。 關於身分識別-哪一種物件是它是參考型別？ 基於這個理由，「 參考類型 」 也稱為 「 多型類型 」。  
  
 如果您真的想類似參考的型別 （基底類別，虛擬函式），您需要明確停用複製，如中所示`MyRefType`下列程式碼的類別。  
  
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
  
 編譯上述程式碼會導致下列錯誤：  
  
```Output  
test.cpp(15) : error C2248: 'MyRefType::operator =' : cannot access private member declared in class 'MyRefType'  
        meow.cpp(5) : see declaration of 'MyRefType::operator ='  
        meow.cpp(3) : see declaration of 'MyRefType'  
```  
  
## <a name="value-types-and-move-efficiency"></a>實值型別，並移動效率  
 因為新複製的最佳化，可以避免複製配置的負荷。 比方說，當您插入的字串向量中間字串，會有任何複本重新配置額外負荷，只移動-即使它會造成本身向量的成長。 這也適用於其他作業，例如執行兩個非常大型的物件上的加入作業。 您要如何讓這些值的作業最佳化？ 中某些 c + + 編譯器中，編譯器將這為您啟用隱含的如同由編譯器可以自動產生複製建構函式。 不過，在 Visual c + + 中，您的類別必須為 「 選擇加入 」 類別定義中宣告的方式移動指派和建構函式。 這透過使用雙連字號 (& &) 函式宣告和定義的移動建構函式和移動指派方法，在適當的成員中的右值參考。  您也需要插入正確的程式碼，以從來源物件的 「 竊取內容 」。  
  
 如何決定是否您需要移動已啟用？ 如果您已經知道您需要將複製建構已啟用，您可能需要移動已啟用，如果它可以是成本較低，比的深層複本。 不過，如果您知道您需要移動的支援，它不一定表示您想要啟用的複本。 後者的情況下會稱為 「 僅限移動類型 」。 已在標準程式庫範例`unique_ptr`。 附帶一提，舊`auto_ptr`已被取代，並已取代`unique_ptr`因為缺乏的移動語意支援舊版的 c + + 中。  
  
 使用移動語意，您可以傳回值或插入中介。 移動已複製的最佳化。 沒有因應措施的堆積配置的需要。 請考慮下列虛擬程式碼：  
  
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
 對於類似值的類別，可以更便宜的深層複本比移動，啟用移動建構函式和移動指派，以提升效率。 請考慮下列虛擬程式碼：  
  
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
  
 如果您啟用複製建構/指派，也啟用移動建構/指派，如果它可以是成本較低，比的深層複本。  
  
 有些*非實值*類型是僅限移動，例如當您無法複製資源時，只傳送擁有權。 範例：`unique_ptr`。  
  
## <a name="section"></a>區段  
 內容  
  
## <a name="see-also"></a>另請參閱  
 [C + + 類型系統](../cpp/cpp-type-system-modern-cpp.md)   
 [歡迎回到 c + +](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C++ 語言參考](../cpp/cpp-language-reference.md)   
 [C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)