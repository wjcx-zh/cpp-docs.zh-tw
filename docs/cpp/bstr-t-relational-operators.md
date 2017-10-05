---
title: "_bstr_t 關係運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator>
- _bstr_t::operator==
- _bstr_t::operator>=
- _bstr_t::operator!=
- _bstr_t::operator<
- _bstr_t::operator<=
- _bstr_t::operator!
dev_langs:
- C++
helpviewer_keywords:
- '>= operator, comparing specific objects'
- operator<=, bstr
- '!= operator'
- operator ==, bstr
- operator!=, relational operators
- < operator, comparing specific objects
- relational operators, _bstr_t class
- operator==, bstr
- <= operator, with specific objects
- operator <=, bstr
- operator >=, bstr
- operator !=, relational operators
- '> operator, comparing specific objects'
- operator<, bstr
- == operator, with specific Visual C++ objects
- operator>=, bstr
- operator <, bstr
- operator >, bstr
ms.assetid: e153da72-37c3-4d8a-b8eb-730d65da64dd
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 4af54cf348765453fea3dd59959e00f623bef7e0
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="bstrt-relational-operators"></a>_bstr_t 關係運算子
**Microsoft 特定的**  
  
 比較兩個 `_bstr_t` 物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
      bool operator!( ) const throw( );   
bool operator==(  
   const _bstr_t& str   
) const throw( );  
bool operator!=(  
   const _bstr_t& str   
) const throw( );  
bool operator<(  
   const _bstr_t& str   
) const throw( );  
bool operator>(  
   const _bstr_t& str   
) const throw( );  
bool operator<=(  
   const _bstr_t& str   
) const throw( );  
bool operator>=(  
   const _bstr_t& str   
) const throw( );  
```  
  
## <a name="remarks"></a>備註  
 這些運算子會針對兩個 `_bstr_t` 物件進行字彙上的比較。 運算子會傳回**true**如果比較有效，否則傳回**false**。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_bstr_t 類別](../cpp/bstr-t-class.md)
