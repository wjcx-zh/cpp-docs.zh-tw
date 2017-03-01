---
title: "move_iterator 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.move_iterator
- move_iterator
- iterator/std::move_iterator
- std::move_iterator
dev_langs:
- C++
helpviewer_keywords:
- move_iterator class
ms.assetid: a5e5cdd8-a264-4c6b-9f9c-68b0e8edaab7
caps.latest.revision: 20
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
ms.sourcegitcommit: 2d05749ba2837a3879c91886b9266de47dd2ece6
ms.openlocfilehash: b689b6363fbe7eff8d34d709f451e46bf9a92537
ms.lasthandoff: 02/24/2017

---
# <a name="moveiterator-class"></a>move_iterator 類別
類別樣板 `move_iterator` 是迭代器的包裝函式。 move_iterator 和它所包裝 (儲存) 的迭代器提供相同的行為，不過，它會將預存迭代器的取值運算子變更為右值參考，而將複製變成移動。 如需有關 rvalue 的詳細資訊，請參閱 [Rvalue 參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## <a name="syntax"></a>語法  
```
class move_iterator;  
```
## <a name="remarks"></a>備註  
 此樣板類別描述行為類似迭代器的物件 (除非取值時)。 它會儲存 `Iterator` 類型的隨機存取迭代器，此迭代器可透過成員函式 `base``()` 來存取。 `move_iterator` 的所有作業是直接在預存迭代器上執行，不過，`operator*` 的結果會隱含轉型為 `value_type&&` 以建立右值參考。  
  
 `move_iterator` 可能會執行包裝的迭代器所未定義的作業。 不應該使用這些作業。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[move_iterator](#move_iterator__move_iterator)|`move_iterator` 類型物件的建構函式。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[move_iterator::iterator_type](#move_iterator__iterator_type)|`RandomIterator` 樣板參數的同義字。|  
|[move_iterator::iterator_category](#move_iterator__iterator_category)|同名、較長 `typename` 運算式的同義字，`iterator_category` 識別迭代器的一般功能。|  
|[move_iterator::value_type](#move_iterator__value_type)|同名、較長 `typename` 運算式的同義字，`value_type` 描述迭代器項目的類型。|  
|[move_iterator::difference_type](#move_iterator__difference_type)|同名、較長 `typename` 運算式的同義字，`difference_type` 描述表示項目之間的差異值所需的整數類資料類型。|  
|[move_iterator::pointer](#move_iterator__pointer)|`RandomIterator` 樣板參數的同義字。|  
|[move_iterator::reference](#move_iterator__reference)|`rvalue` 參考 `value_type&&` 的同義字。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[move_iterator::base](#move_iterator__base)|成員函式傳回這個 `move_iterator` 所包裝的預存迭代器。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[move_iterator::operator*](#move_iterator__operator_star)|傳回 `(reference)*``base``().`。|  
|[move_iterator::operator++](#move_iterator__operator_add_add)|遞增預存迭代器。 確切行為取決於它是否前置遞增或後置遞增作業。|  
|[move_iterator::operator--](#move_iterator__operator--)|遞減預存迭代器。 確切行為取決於它是否前置遞減或後置遞減作業。|  
|[move_iterator::operator-&gt;](#move_iterator__operator-_gt_)|傳回 `&**this`。|  
|[move_iterator::operator-](#move_iterator__operator-)|藉由先從目前位置減去右值來傳回 `move_iterator(*this) -=`。|  
|[move_iterator::operator[]](#move_iterator__operator_at)|傳回 `(reference)*(*this + off)`。 可讓您指定距離目前基底的位移，取得該位置上的值。|  
|[move_iterator::operator+](#move_iterator__operator_add)|傳回 `move_iterator(*this) +=` 值。 可讓您將位移加入至基底，取得該位置上的值。|  
|[move_iterator::operator+=](#move_iterator__operator_add_eq)|將右值加入到預存迭代器，並傳回 `*this`。|  
|[move_iterator::operator-=](#move_iterator__operator-_eq)|從預存迭代器減去右值，並傳回 `*this`。|  
  
## <a name="requirements"></a>需求  
 **標頭：**\<iterator>  
  
 **命名空間：** std  
  
##  <a name="a-namemoveiteratorbasea--moveiteratorbase"></a><a name="move_iterator__base"></a>  move_iterator::base  
 傳回此 `move_iterator` 的預存迭代器。  
  
```
RandomIterator base() const;
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回儲存的迭代器。  
  
##  <a name="a-namemoveiteratordifferencetypea--moveiteratordifferencetype"></a><a name="move_iterator__difference_type"></a>  move_iterator::difference_type  
 `difference_type` 類型是以迭代器特性 `difference_type` 為基礎的 `move_iterator``typedef`，可與其交替使用。  
  
```
typedef typename iterator_traits<RandomIterator>::difference_type difference_type;
```    
  
### <a name="remarks"></a>備註  
 這個類型與迭代器特性 `typename iterator_traits<RandomIterator>::pointer` 同義。  
  
##  <a name="a-namemoveiteratoriteratorcategorya--moveiteratoriteratorcategory"></a><a name="move_iterator__iterator_category"></a>  move_iterator::iterator_category  
 `iterator_category` 類型是以迭代器特性 `iterator_category` 為基礎的 `move_iterator``typedef`，可與其交替使用。  
  
```
typedef typename iterator_traits<RandomIterator>::iterator_category  iterator_category;
```    
  
### <a name="remarks"></a>備註  
 這個類型與迭代器特性 `typename iterator_traits<RandomIterator>::iterator_category` 同義。  
  
##  <a name="a-namemoveiteratoriteratortypea--moveiteratoriteratortype"></a><a name="move_iterator__iterator_type"></a>  move_iterator::iterator_type  
 `iterator_type` 類型以類別範本 `move_iterator` 的範本參數 `RandomIterator` 為基礎，可與其交替使用。  
  
```
typedef RandomIterator iterator_type;
```  
  
### <a name="remarks"></a>備註  
 此類型是樣板參數 `RandomIterator` 的同義字。  
  
##  <a name="a-namemoveiteratormoveiteratora--moveiteratormoveiterator"></a><a name="move_iterator__move_iterator"></a>  move_iterator::move_iterator  
 建構移動迭代器。 這個參數可當做預存迭代器使用。  
  
```
move_iterator();
explicit move_iterator(RandomIterator right);
template <class Type>
move_iterator(const move_iterator<Type>& right);
```  
  
### <a name="parameters"></a>參數  
 `right`  
 要當做預存迭代器使用的迭代器。  
  
### <a name="remarks"></a>備註  
 第一個建構函式會使用預存迭代器的預設建構函式來初始化迭代器。 其餘建構函式則會使用 `base.base()` 來初始化預存迭代器。  
  
##  <a name="a-namemoveiteratoroperatoraddeqa--moveiteratoroperator"></a><a name="move_iterator__operator_add_eq"></a>  move_iterator::operator+=  
 將位移加入預存迭代器，以便此預存迭代器指向目前新位置的項目。 然後運算子再移動新的目前項目。  
  
```
move_iterator& operator+=(difference_type _Off);
```  
  
### <a name="parameters"></a>參數  
 `_Off`  
 要加入至目前位置的位移，藉以判斷目前新位置。  
  
### <a name="return-value"></a>傳回值  
 傳回新的目前項目。  
  
### <a name="remarks"></a>備註  
 此運算子會將 `_Off` 加入該預存迭代器。 接著傳回 `*this`。  
  
##  <a name="a-namemoveiteratoroperator-eqa--moveiteratoroperator-"></a><a name="move_iterator__operator-_eq"></a>  move_iterator::operator-=  
 在指定數目的先前項目之間移動。 這個運算子會從預存迭代器減去位移。  
  
```
move_iterator& operator-=(difference_type _Off);
```  
  
### <a name="parameters"></a>參數  
  
### <a name="remarks"></a>備註  
 運算子會評估 `*this += -_Off`。 接著傳回 `*this`。  
  
##  <a name="a-namemoveiteratoroperatoraddadda--moveiteratoroperator"></a><a name="move_iterator__operator_add_add"></a>  move_iterator::operator++  
 遞增預存迭代器，其屬於此 `move_iterator.`。目前項目會由後置遞增運算子存取。 下個項目由前置遞增運算子存取。  
  
```
move_iterator& operator++();
move_iterator operator++(int);
```  
  
### <a name="parameters"></a>參數  
  
### <a name="remarks"></a>備註  
 第一個 (前置遞增) 運算子會遞增預存迭代器。 接著傳回 `*this`。  
  
 第二個 (後置遞增) 運算子會複製 `*this`，並評估 `++*this`。 接著傳回複本。  
  
##  <a name="a-namemoveiteratoroperatoradda--moveiteratoroperator"></a><a name="move_iterator__operator_add"></a>  move_iterator::operator+  
 傳回前進任意項目數的迭代器位置。  
  
```
move_iterator operator+(difference_type _Off) const;
```  
  
### <a name="parameters"></a>參數  
  
### <a name="remarks"></a>備註  
 此運算子會傳回 `move_iterator(*this) +=` `_Off`。  
  
##  <a name="a-namemoveiteratoroperatorata--moveiteratoroperator"></a><a name="move_iterator__operator_at"></a>  move_iterator::operator[]  
 允許陣列索引存取 `move iterator` 範圍內的元素。  
  
```
reference operator[](difference_type _Off) const;
```  
  
### <a name="parameters"></a>參數  
  
### <a name="remarks"></a>備註  
 第一個運算子會傳回 `(reference)*(*this + _Off)`。  
  
##  <a name="a-namemoveiteratoroperator--a--moveiteratoroperator--"></a><a name="move_iterator__operator--"></a>  move_iterator::operator--  
 前置遞減和後置遞減成員運算子會在預存迭代器上執行遞減。  
  
```
move_iterator& operator--();
move_iterator operator--();
```  
  
### <a name="parameters"></a>參數  
  
### <a name="remarks"></a>備註  
 第一個成員運算子 (前置遞減) 會遞減預存迭代器。 接著傳回 `*this`。  
  
 第二個 (後置遞減) 運算子會複製 `*this`，並評估 `--*this`。 接著傳回複本。  
  
##  <a name="a-namemoveiteratoroperator-a--moveiteratoroperator-"></a><a name="move_iterator__operator-"></a>  move_iterator::operator-  
 將預存迭代器遞減並傳回指定的值。  
  
```
move_iterator operator-(difference_type _Off) const;
```  
  
### <a name="parameters"></a>參數  
  
### <a name="remarks"></a>備註  
 第一個運算子會傳回 `move_iterator(*this) -= _Off`。  
  
##  <a name="a-namemoveiteratoroperatorstara--moveiteratoroperator"></a><a name="move_iterator__operator_star"></a>  move_iterator::operator*  
 取值預存迭代器並傳回值。 這個行為類似 `rvalue reference` 並會執行移動指派。 這個運算子會將目前項目傳送到基底迭代器之外。 後面的項目會成為新的目前項目。  
  
```
reference operator*() const;
```  
  
### <a name="remarks"></a>備註  
 第一個運算子會傳回 `(reference)*``base``()`。  
  
##  <a name="a-namemoveiteratoroperator-gta--moveiteratoroperator-gt"></a><a name="move_iterator__operator-_gt_"></a>  move_iterator::operator-&gt;  
 與一般 `RandomIterator``operator->` 一樣，它也可用來存取屬於目前元素的欄位。  
  
```
pointer operator->() const;
```  
  
### <a name="remarks"></a>備註  
 第一個運算子會傳回 `&**this`。  
  
##  <a name="a-namemoveiteratorpointera--moveiteratorpointer"></a><a name="move_iterator__pointer"></a>  move_iterator::pointer  
 `pointer` 類型是以 `move_iterator` 的隨機迭代器 `RandomIterator` 為基礎的 `typedef`，可交替使用。  
  
```
typedef RandomIterator  pointer;
```    
  
### <a name="remarks"></a>備註  
 此類型是 `RandomIterator` 的同義字。  
  
##  <a name="a-namemoveiteratorreferencea--moveiteratorreference"></a><a name="move_iterator__reference"></a>  move_iterator::reference  
 類型 `reference` 是一個 `typedef`，以 `move_iterator` 的 `value_type&&` 為基礎，可與 `value_type&&` 交替使用。  
  
```
typedef value_type&& reference;
```    
  
### <a name="remarks"></a>備註  
 此類型與 `value_type&&` 同義，後者是一個 rvalue 參考。  
  
##  <a name="a-namemoveiteratorvaluetypea--moveiteratorvaluetype"></a><a name="move_iterator__value_type"></a>  move_iterator::value_type  
 `value_type` 類型是以迭代器特性 `value_type` 為基礎的 `move_iterator``typedef`，可與其交替使用。  
  
```
typedef typename iterator_traits<RandomIterator>::value_type   value_type;
```    
  
### <a name="remarks"></a>備註  
 這個類型與迭代器特性 `typename iterator_traits<RandomIterator>::value_type` 同義。  
  
## <a name="see-also"></a>另請參閱  
 [\<iterator>](../standard-library/iterator.md)   
 [Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)   
 [移動建構函式和移動指派運算子 (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)





