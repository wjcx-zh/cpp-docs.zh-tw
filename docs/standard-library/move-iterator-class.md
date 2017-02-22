---
title: "move_iterator 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.move_iterator"
  - "move_iterator"
  - "iterator/std::move_iterator"
  - "std::move_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "move_iterator 類別"
ms.assetid: a5e5cdd8-a264-4c6b-9f9c-68b0e8edaab7
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# move_iterator 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

類別樣板 `move_iterator` 是迭代器的包裝函式。  move\_iterator 和它所包裝 \(儲存\) 的迭代器提供相同的行為，不過，它會將預存迭代器的取值運算子變更為右值參考，而將複製變成移動。  如需右值的詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## 語法  
  
```  
template<class Iterator>  
    class move_iterator {  
public:  
    typedef Iterator iterator_type;  
    typedef typename      
        iterator_traits<Iterator>::iterator_category  
            iterator_category;  
    typedef typename iterator_traits<Iterator>::value_type  
        value_type;  
    typedef typename iterator_traits<Iterator>::difference_type  
        difference_type;  
    typedef Iterator  
        pointer;  
    typedef value_type&&  
        reference;  
  
    move_iterator();  
    explicit move_iterator (Iterator right);  
    template<class Type>  
        move_iterator (const move_iterator<Type>& right);  
    template <class Type>   
        move_iterator& operator=(const move_iterator<Type>& right);  
  
    iterator_type base () const;  
    reference operator* () const;  
    pointer operator-> () const;  
  
    move_iterator& operator++ ();  
    move_iterator operator++ (int);  
    move_iterator& operator-- ();  
    move_iterator operator-- (int);  
  
    move_iterator& operator+= (difference_type off);  
    move_iterator operator+ (difference_type off) const;  
    move_iterator& operator-= (difference_type off);  
    move_iterator operator- (difference_type off) const;  
    reference operator[] (difference_type off) const;  
    };  
```  
  
## 備註  
 此樣板類別描述行為類似迭代器的物件 \(除非取值時\)。  它儲存 `Iterator` 類型的隨機存取迭代器，透過成員函式 `base``()` 進行存取。  `move_iterator` 的所有作業是直接在預存迭代器上執行，不過，`operator*` 的結果會隱含轉型為 `value_type&&` 以建立右值參考。  
  
 `move_iterator` 可能會執行包裝的迭代器所未定義的作業。  不應該使用這些作業。  
  
### 建構函式  
  
|||  
|-|-|  
|[move\_iterator](../Topic/move_iterator::move_iterator.md)|`move_iterator` 類型物件的建構函式。|  
  
### Typedef  
  
|||  
|-|-|  
|[move\_iterator::iterator\_type](../Topic/move_iterator::iterator_type.md)|`RandomIterator` 樣板參數的同義字。|  
|[move\_iterator::iterator\_category](../Topic/move_iterator::iterator_category.md)|同名、較長 `typename` 運算式的同義字，`iterator_category` 識別迭代器的一般功能。|  
|[move\_iterator::value\_type](../Topic/move_iterator::value_type.md)|同名、較長 `typename` 運算式的同義字，`value_type` 描述迭代器項目的類型。|  
|[move\_iterator::difference\_type](../Topic/move_iterator::difference_type.md)|同名、較長 `typename` 運算式的同義字，`difference_type` 描述表示項目之間的差異值所需的整數類資料類型。|  
|[move\_iterator::pointer](../Topic/move_iterator::pointer.md)|`RandomIterator` 樣板參數的同義字。|  
|[move\_iterator::reference](../Topic/move_iterator::reference.md)|`rvalue` 參考 `value_type&&` 的同義字。|  
  
### 成員函式  
  
|||  
|-|-|  
|[move\_iterator::base](../Topic/move_iterator::base.md)|成員函式傳回這個 `move_iterator` 所包裝的預存迭代器。|  
  
### 運算子  
  
|||  
|-|-|  
|[move\_iterator::operator\*](../Topic/move_iterator::operator*.md)|傳回 `(reference)*``base``().`|  
|[move\_iterator::operator\+\+](../Topic/move_iterator::operator++.md)|遞增預存迭代器。  確切行為取決於它是否前置遞增或後置遞增作業。|  
|[move\_iterator::operator\-\-](../Topic/move_iterator::operator--.md)|遞減預存迭代器。  確切行為取決於它是否前置遞減或後置遞減作業。|  
|[move\_iterator::operator\-\>](../Topic/move_iterator::operator-%3E.md)|傳回 `&**this`。|  
|[move\_iterator::operator\-](../Topic/move_iterator::operator-.md)|先從目前位置減去右值，傳回 `move_iterator(*this) -=` 。|  
|[move\_iterator::operator](../Topic/move_iterator::operator.md)|傳回 `(reference)*(*this + off)`。  可讓您指定距離目前基底的位移，取得該位置上的值。|  
|[move\_iterator::operator\+](../Topic/move_iterator::operator+.md)|傳回 `move_iterator(*this) +=` 值。  可讓您將位移加入至基底，取得該位置上的值。|  
|[move\_iterator::operator\+\=](../Topic/move_iterator::operator+=.md)|將右值加入到預存迭代器，並傳回 `*this`。|  
|[move\_iterator::operator\-\=](../Topic/move_iterator::operator-=.md)|從預存迭代器減去右值，並傳回 `*this`。|  
  
## 需求  
 **標頭：**\<iterator\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<iterator\>](../standard-library/iterator.md)   
 [Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)   
 [移動建構函式和移動指派運算子 \(C\+\+\)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)