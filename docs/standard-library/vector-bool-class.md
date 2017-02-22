---
title: "vector&lt;bool&gt; 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vector<bool>"
  - "std.vector<bool>"
  - "std::vector<bool>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "< bool > vector 類別"
ms.assetid: 8028c8ed-ac9c-4f06-aba1-5de45c00aafb
caps.latest.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 29
---
# vector&lt;bool&gt; 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

 `vector<bool>` 類別是部分特製化 [向量](../standard-library/vector-class.md) 類型項目的 `bool`。 它具有特製化所使用基礎類型的配置器，透過每個位元儲存一個 `bool` 值來提供空間最佳化。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Allocator = allocator<bool>>  
class vector<bool, Allocator>  
```  
  
## <a name="remarks"></a>備註  
 這個類別樣板特製化的行為類似向量，除了在本文中說明差異之處。  
  
 處理 `bool` 類型的作業會對應至容器儲存體中的值。 `allocator_traits::construct` 不用來建構這些值。  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[const_pointer](#vector_lt_bool_gt___const_pointer)|`const_iterator` 的 typedef，可做為常數指標指向 `vector<bool>` 的布林值項目。|  
|[const_reference](#vector_lt_bool_gt___const_reference)|`bool` 的 typedef。 在初始化之後，就無法觀察原始值的更新。|  
|[指標](#vector_lt_bool_gt___pointer)|`iterator` 的 typedef，可做為指標指向 `vector<bool>` 的布林值項目。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[翻轉](#vector_lt_bool_gt___flip)|會反轉 `vector<bool>` 中的所有位元。|  
|[交換](#vector_lt_bool_gt___swap)|交換兩個 `vector<bool>` 的項目。|  
|[運算子 &#91; & #93。](#vector_lt_bool_gt___operator_at)|傳回在指定位置上 `vector<bool>` 項目的模擬參考。|  
|`at`|函數一樣特製化 [向量](../standard-library/vector-class.md):: 在函式，但它使用 proxy 類別 [向量 \< bool>:: 參考](#vector_lt_bool_gt___reference_class)。 另請參閱 [運算子 &#91; &#93;](#vector_lt_bool_gt___operator_at)。|  
|`front`|函數一樣特製化 [向量](../standard-library/vector-class.md):: 最上層函式，它會使用 proxy 類別 [向量 \< bool>:: 參考](#vector_lt_bool_gt___reference_class)。 另請參閱 [運算子 &#91; &#93;](#vector_lt_bool_gt___operator_at)。|  
|`back`|函數一樣特製化 [向量](../standard-library/vector-class.md):: 回函式，它會使用 proxy 類別 [向量 \< bool>:: 參考](#vector_lt_bool_gt___reference_class)。 另請參閱 [運算子 &#91; &#93;](#vector_lt_bool_gt___operator_at)。|  
  
### <a name="proxy-class"></a>Proxy 類別  
  
|||  
|-|-|  
|[向量 \< bool> 參考類別](#vector_lt_bool_gt___reference_class)|類別，做為 Proxy 以模擬 `bool&` 行為，而且其物件可以提供對 `vector<bool>` 物件中項目 (單一位元) 的參考。|  
  
## <a name="requirements"></a>需求  
 **標頭**: \< 向量>  
  
 **命名空間：** std  
  
##  <a name="a-namevectorltboolgtconstpointera-vectorboolconstpointer"></a><a name="vector_lt_bool_gt___const_pointer"></a>  向量 \< bool>:: const_pointer  
 類型，描述可以做為常數指標的物件，指向由 `vector<bool>` 物件所包含序列的布林值項目。  
  
```  
typedef const_iterator const_pointer;  
```  
  
##  <a name="a-namevectorltboolgtconstreferencea-vectorboolconstreference"></a><a name="vector_lt_bool_gt___const_reference"></a>  向量 \< bool>:: const_reference  
 類型，描述可以做為常數參考的物件，指向由 `vector<bool>` 物件所包含序列的布林值項目。  
  
```  
typedef bool const_reference;  
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊和程式碼範例，請參閱 [向量&lt;bool&gt;:: operator =](#vector_lt_bool_gt___reference_operator_eq)。  
  
##  <a name="a-namevectorltboolgtflipa-vectorboolflip"></a><a name="vector_lt_bool_gt___flip"></a>  向量 \< bool>:: flip  
 會反轉 `vector<bool>` 中的所有位元。  
  
```  
void flip();
```  
  
### <a name="example"></a>範例  
  
```cpp  
// vector_bool_flip.cpp  
// compile with: /EHsc /W4  
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    cout << boolalpha; // format output for subsequent code  
  
    vector<bool> vb = { true, false, false, true, true };  
    cout << "The vector is:" << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
  
    vb.flip();  
  
    cout << "The flipped vector is:" << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
}  
  
```  
  
##  <a name="a-namevectorltboolgtoperatorata-vectorbooloperator"></a><a name="vector_lt_bool_gt___operator_at"></a>  向量 \< bool>:: operator]  
 傳回在指定位置上 `vector<bool>` 項目的模擬參考。  
  
```  
vector<bool>::reference operator[](size_type Pos);

vector&<bool&>::const_reference operator[](size_type Pos) const;
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|`Pos`|`vector<bool>` 項目的位置。|  
  
### <a name="return-value"></a>傳回值  
 A [向量 \< bool>:: 參考](#vector_lt_bool_gt___reference_class) 或 [向量 \< bool>:: const_reference](#vector_lt_bool_gt___const_reference) 物件，包含索引項目的值。  
  
 如果指定的位置大於或等於容器大小，則結果是未定義。  
  
### <a name="remarks"></a>備註  
 如果在 `_ITERATOR_DEBUG_LEVEL` 設定時編譯，當您嘗試存取在向量界限以外的項目時，會發生執行階段錯誤。  如需詳細資訊，請參閱 [Checked Iterators](../standard-library/checked-iterators.md)。  
  
### <a name="example"></a>範例  
  這個程式碼範例會示範 `vector<bool>::operator[]` 的正確用法和兩個常見的程式碼錯誤 (已標記為註解)。 這些會造成錯誤，因為 `vector<bool>::reference` 所傳回 `vector<bool>::operator[]` 物件的位址無法採用。  
  
```cpp  
  
// cl.exe /EHsc /nologo /W4 /MTd   
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    cout << boolalpha;  
    vector<bool> vb;  
  
    vb.push_back(true);  
    vb.push_back(false);  
  
    //    bool* pb = &vb[1]; // conversion error -                         do not use  
    //    bool& refb = vb[1];   // conversion error -                         do not use  
    bool hold = vb[1];  
    cout << "The second element of vb is " << vb[1] << endl;  
    cout << "The held value from the second element of vb is " << hold << endl;  
  
    // Note this doesn't modify hold.  
    vb[1] = true;  
    cout << "The second element of vb is " << vb[1] << endl;  
    cout << "The held value from the second element of vb is " << hold << endl;  
}  
  
```  
  
##  <a name="a-namevectorltboolgtpointera-vectorboolpointer"></a><a name="vector_lt_bool_gt___pointer"></a>  向量 \< bool>:: 指標  
 類型，描述可以做為指標的物件，指向由 `vector<bool>` 物件所包含序列的布林值項目。  
  
```  
typedef iterator pointer;  
```  
  
##  <a name="a-namevectorltboolgtreferenceclassa-vectorboolreference-class"></a><a name="vector_lt_bool_gt___reference_class"></a>  向量 \< bool>:: reference 類別  
  `vector<bool>::reference` 類別是提供的 proxy 類別 [向量 \< bool> 類別](../standard-library/vector-bool-class.md) 模擬 `bool&`。  
  
### <a name="remarks"></a>備註  
 需要模擬參考，因為 C++ 原生不允許對位元的直接參考。 `vector<bool>` 對每個項目只使用一個位元，您可以使用這個 Proxy 類別來參考位元。 不過，因為某些指派無效，參考模擬不完整。 例如，因為位址 `vector<bool>::reference` 無法取得物件，使用下列程式碼 [向量 \< bool>:: 運算子 &#91; &#93;](#vector_lt_bool_gt___operator_at) 不正確︰  
  
```cpp  
    vector<bool> vb;  
...  
    bool* pb = &vb[1]; // conversion error -         do not use  
    bool& refb = vb[1];   // conversion error -         do not use  
```  
  
###  <a name="a-namevectorltboolgtreferenceflipa-vectorboolreferenceflip"></a><a name="vector_lt_bool_gt___reference_flip"></a>  向量 \< bool>:: reference:: flip  
 反轉所參考的布林值 [向量 \< bool>](../standard-library/vector-bool-class.md) 項目。  
  
```  
void flip();
```  
  
#### <a name="remarks"></a>備註  
  
#### <a name="example"></a>範例  
  
```cpp  
// vector_bool_ref_flip.cpp  
// compile with: /EHsc /W4  
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    cout << boolalpha;  
  
    vector<bool> vb = { true, false, false, true, true };  
  
    cout << "The vector is: " << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
  
    vector<bool>::reference vbref = vb.front();  
    vbref.flip();  
  
    cout << "The vector with first element flipped is: " << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
}  
/* Output:  
The vector is:  
    true false false true true  
The vector with first element flipped is:  
    false false false true true  
    */  
  
```  
  
###  <a name="a-namevectorltboolgtreferenceoperatorboola-vectorboolreferenceoperator-bool"></a><a name="vector_lt_bool_gt___reference_operator_bool"></a>  向量 \< bool>:: operator bool  
 提供從 `vector<bool>::reference` 至 `bool` 的隱含轉換。  
  
'' 運算子 bool() const;
```  
  
#### Return Value  
 The Boolean value of the element of the vector<bool\> object.  
  
#### Remarks  
 The `vector<bool>` object cannot be modified by this operator.  
  
###  <a name="vector_lt_bool_gt___reference_operator_eq"></a>  vector<bool\>::reference::operator=  
 Assigns a Boolean value to a bit, or the value held by a referenced element to a bit.  
  
```  
運算子 & 參考 = （const 參考和右）。

運算子 & 參考 =(bool Val);
```  
  
#### Parameters  
 `Right`  
 The element reference whose value is to be assigned to the bit.  
  
 `Val`  
 The Boolean value to be assigned to the bit.  
  
#### Example  
  
```cpp  
// vector_bool_ref_op_assign.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
#include <string>  
  
using namespace std;  
  
template <typename C> void print(const string& s, const C& c) {  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    cout << boolalpha;  
  
    vector<bool> vb = { true, false, false, true, true };  
  
    print("The vector is: ", vb);  
  
    // Invoke vector<bool>::reference::operator=()  
    vector<bool>::reference refelem1 = vb[0];  
    vector<bool>::reference refelem2 = vb[1];  
    vector<bool>::reference refelem3 = vb[2];  
  
    bool b1 = refelem1;  
    bool b2 = refelem2;  
    bool b3 = refelem3;  
    cout << "The original value of the 1st element stored in a bool: " << b1 << endl;  
    cout << "The original value of the 2nd element stored in a bool: " << b2 << endl;  
    cout << "The original value of the 3rd element stored in a bool: " << b3 << endl;  
    cout << endl;  
  
    refelem2 = refelem1;  
  
    print("The vector after assigning refelem1 to refelem2 is now: ", vb);  
  
    refelem3 = true;  
  
    print("The vector after assigning false to refelem1 is now: ", vb);  
  
    // The initial values are still stored in the bool variables and remained unchanged  
    cout << "The original value of the 1st element still stored in a bool: " << b1 << endl;  
    cout << "The original value of the 2nd element still stored in a bool: " << b2 << endl;  
    cout << "The original value of the 3rd element still stored in a bool: " << b3 << endl;  
    cout << endl;  
}  
/* Output:  
The vector is: true false false true true  
The original value of the 1st element stored in a bool: true  
The original value of the 2nd element stored in a bool: false  
The original value of the 3rd element stored in a bool: false  
  
The vector after assigning refelem1 to refelem2 is now: true true false true true  
The vector after assigning false to refelem1 is now: true true true true true  
The original value of the 1st element still stored in a bool: true  
The original value of the 2nd element still stored in a bool: false  
The original value of the 3rd element still stored in a bool: false  
*/  
  
```  
  
##  <a name="a-namevectorltboolgtswapa-vectorboolswap"></a><a name="vector_lt_bool_gt___swap"></a>  向量 \< bool>:: swap  
 交換兩個布林值向量的項目的靜態成員函式 ( `vector<bool>`) 所使用的 proxy 類別 [向量 \< bool>:: 參考](#vector_lt_bool_gt___reference_class)。  
  
```  
 
static void swap(
    reference Left,  
    reference Right);
```  
  
### <a name="parameters"></a>參數  
 `Left`  
 要與 `Right` 項目交換的項目。  
  
 `Right`  
 要與 `Left` 項目交換的項目。  
  
### <a name="remarks"></a>備註  
 這個多載支援 `vector<bool>` 的特別 Proxy 需求。 [向量](../standard-library/vector-class.md):: swap 具有相同的功能，為單一引數多載的 `vector<bool>::swap()`。  
  
## <a name="see-also"></a>另請參閱  
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)

