---
title: "initializer_list 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 1f2c0ff4-5636-4f79-b008-e75426e3d2ab
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: 2ac3e7fa456e5d3ff04bc5d974c87a9cbb055fea
ms.lasthandoff: 02/24/2017

---
# <a name="initializerlist-class"></a>initializer_list 類別
提供對項目的陣列之存取，其中每個成員都有指定的類型。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Type>  
class initializer_list
```  
  
#### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`Type`|要存放在 `initializer_list` 中的項目資料類型。|  

  
## <a name="remarks"></a>備註  
 可以使用括號初始設定式清單建構 `initializer_list`：  
  
```cpp  
initializer_list<int> i1{ 1, 2, 3, 4 };  
```  
  
 每當函式簽章需要 `initializer_list` 時，編譯器會將以大括號括住且具有同質項目的初始設定式清單轉換至 `initializer_list`。 如需有關使用 `initializer_list` 的更多詳細資料，請參閱[統一初始設定和委派建構函式](../cpp/uniform-initialization-and-delegating-constructors.md)  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[initializer_list](../standard-library/forward-list-class.md#forward_list__forward_list)|建構類型 `initializer_list` 的物件。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|value_type|`initializer_list` 中的項目類型。|  
|參考|類型，提供在 `initializer_list` 中之項目的參考。|  
|const_reference|類型，提供在 `initializer_list` 中之項目的常數參考。|  
|size_type|代表 `initializer_list` 中項目數的類型。|  
|迭代器|提供 `initializer_list` 之迭代器的類型。|  
|const_iterator|提供 `initializer_list` 之常數迭代器的類型。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[begin](#initializer_list__begin)|傳回 `initializer_list` 中第一個項目的指標。|  
|[end](#initializer_list__end)|傳回超出 `initializer_list` 中最後一個項目的項目指標。|  
|[size](#initializer_list__size)|傳回 `initializer_list` 中項目的數目。|  
  
## <a name="requirements"></a>需求  
 **標頭：**\<initializer_list>  
  
 **命名空間：** std  
  
##  <a name="a-nameinitializerlistbegina--initializerlistbegin"></a><a name="initializer_list__begin"></a>  initializer_list::begin  
 傳回 `initializer_list` 中第一個項目的指標。  
  
```  
constexpr const InputIterator* begin() const noexcept;  
```  
  
### <a name="return-value"></a>傳回值  
 指向 `initializer_list` 第一個項目的指標。 如果此清單是空的，則該清單開頭和結尾的指標相同。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameinitializerlistenda--initializerlistend"></a><a name="initializer_list__end"></a>  initializer_list::end  
 傳回超出 `initializer list` 中最後一個項目的項目指標。  
  
```  
constexpr const InputIterator* end() const noexcept;  
```  
  
### <a name="return-value"></a>傳回值  
 超出清單中最後一個項目的項目指標。 如果清單是空的，這個指標會與清單中第一個項目的指標相同。  
  
##  <a name="a-nameinitializerlistinitializerlista--initializerlistinitializerlist"></a><a name="initializer_list__initializer_list"></a>  initializer_list::initializer_list  
 建構類型 `initializer_list` 的物件。  
  
```  
constexpr initializer_list() noexcept;
initializer_list(const InputIterator First, const InputIterator Last);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`First`|要複製的元素範圍中第一個元素的位置。|  
|`Last`|超出要複製之元素範圍的第一個元素的位置。|  
  
### <a name="remarks"></a>備註  
 `initializer_list` 的基礎為指定類型的物件陣列。 複製 `initializer_list` 會建立清單的第二個執行個體，指向相同的物件；但不會複製基礎的物件。  
  
### <a name="example"></a>範例  
  
```cpp  
// initializer_list_class.cpp  
// compile with: /EHsc  
#include <initializer_list>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    // Create an empty initializer_list c0  
    initializer_list <int> c0;  
  
    // Create an initializer_list c1 with 1 element  
    initializer_list <int> c1{ 3 };  
  
    // Create an initializer_list c2 with 5 elements   
    initializer_list <int> c2{ 5, 4, 3, 2, 1 };  
  
    // Create a copy, initializer_list c3, of initializer_list c2  
    initializer_list <int> c3(c2);  
  
    // Create a initializer_list c4 by copying the range c3[ first,  last)  
    const int* c3_ptr = c3.begin();  
    c3_ptr++;  
    c3_ptr++;  
    initializer_list <int> c4(c3.begin(), c3_ptr);  
  
    // Move initializer_list c4 to initializer_list c5  
    initializer_list <int> c5(move(c4));  
  
    cout << "c1 =";  
    for (auto c : c1)  
        cout << " " << c;  
    cout << endl;  
  
    cout << "c2 =";  
    for (auto c : c2)  
        cout << " " << c;  
    cout << endl;  
  
    cout << "c3 =";  
    for (auto c : c3)  
        cout << " " << c;  
    cout << endl;  
  
    cout << "c4 =";  
    for (auto c : c4)  
        cout << " " << c;  
    cout << endl;  
  
    cout << "c5 =";  
    for (auto c : c5)  
        cout << " " << c;  
    cout << endl;  
}  
```  
  
```Output  
c1 = 3c2 = 5 4 3 2 1c3 = 5 4 3 2 1c4 = 5 4c5 = 5 4  
```  
  
##  <a name="a-nameinitializerlistsizea--initializerlistsize"></a><a name="initializer_list__size"></a>  initializer_list::size  
 傳回清單中項目的數目。  
  
```  
constexpr size_t size() const noexcept;  
```  
  
### <a name="return-value"></a>傳回值  
 清單中項目的數目。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [<forward_list>](../standard-library/forward-list.md)


