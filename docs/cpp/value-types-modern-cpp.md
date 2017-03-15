---
title: "實值類型 (現代 C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 實值類型 (現代 C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

預設為 C\+\+ 類別是實值型別。  本主題提供實值型別和問題引入概觀與其用途相關。  
  
## 值為參考型別。  
 預設情況下如前所述， C\+\+ 類別是實值型別。  它們可以指定為參考型別，使多型行為支援物件導向程式設計。  實值型別從記憶體配置和控制項的角度有時候被檢視，，而參考型別與基底類別和虛擬函式多型的目的。  根據預設，實值型別可複製，表示永遠具有複製建構函式和複製指派運算子。  對於參考型別，您可讓類別不可複製 \(停用複製建構函式或複製指派運算子\) 和使用虛擬解構函式，支援其預定多型。  實值型別也是關於內容，，，會複製時，永遠都會提供您兩個獨立的值可以個別修改。  參考型別是關於識別–它是何種物件?  因此， 「參考型別」也稱為多型型別」。  
  
 如果您真正想要一個類似參考型別 \(基底類別，虛擬函式\)，如下列程式碼中， `MyRefType` 類別所示您需要明確停用複製，。  
  
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
  
 編譯上述程式碼會產生下列錯誤:  
  
  **test.cpp \(15\):錯誤 C2248:「MyRefType::operator \=」:在類別中宣告的 MyRefType 無法存取私用成員」**  
 **meow.cpp \(5\):請參閱「MyRefType::operator 的宣告 \=」**  
 **meow.cpp \(3\):請參閱「MyRefType "宣告**   
## 實值型別和捲動效率  
 複製配置額外負荷會避免因為的新複本最佳化。  例如，在中，當您在字串的中間向量插入字串，將不會複製重新分配額外負荷，，只有移動，即使它產生向量的長度。  這也適用於其他作業，例如對兩個大型物件的加入作業。  如何使這些值作業最佳化?  在某些 C\+\+ 編譯器，編譯器會隱含地做到這點，您的很像複製建構函式可以由編譯器自動產生。  不過，在 Visual C\+\+ 中，您的類別將需要「選取來宣告它移動工作和建構函式在您的類別定義。  這可以使用在適當的成員函式宣告和定義移動建構函式和移動工作方法的兩個連字號 \(&&\) 右值參考。您也需要插入正確程式碼「竊取粗體量」從來源物件。  
  
 如何決定您是否需要允許捲動?  如果您已經知道需要複製建構允許，您可能想要啟用移動，如果它比深層複本可以便宜。  不過，因此，如果您知道需要移動支援，不一定表示您想要複製允許。  這第二個案例將稱為移動類型」。  一個範例已經在標準程式庫是 `unique_ptr`。  為標記旁，舊的 `auto_ptr` 已由 `unique_ptr` 取代和取代精確因為缺少移到 C\+\+ 舊版的語意支援。  
  
 使用移動語意可以傳回值或插入在中間。  移動是複製的最佳化。  對於堆積配置需要做為運算。  考慮下列虛擬程式碼:  
  
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
  
### 啟用適當的實值型別為基礎的移動  
 若移動超過深層複本可以便宜的值相同的類別，啟用移動建構和移動工作有效率。  考慮下列虛擬程式碼:  
  
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
  
 如果您啟用複製建構\/工作，也請啟用移動建構\/工作，如果它比深層複本可以便宜。  
  
 某些 *非* 實值型別是移動，例如，當您無法複製資源時，，只有轉移擁有權。  範例：`unique_ptr`。  
  
## 區段  
 Content  
  
## 請參閱  
 [C\+\+ 類型系統](../cpp/cpp-type-system-modern-cpp.md)   
 [歡迎回到 C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)   
 [C\+\+ Standard Library](../standard-library/cpp-standard-library-reference.md)