---
title: "_bstr_t 關係運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
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
dev_langs: C++
helpviewer_keywords:
- '>= operator [C++], comparing specific objects'
- operator<= [C++], bstr
- '!= operator'
- operator == [C++], bstr
- operator!= [C++], relational operators
- < operator [C++], comparing specific objects
- relational operators [C++], _bstr_t class
- operator== [C++], bstr
- <= operator [C++], with specific objects
- operator <= [C++], bstr
- operator >= [C++], bstr
- operator != [C++], relational operators
- '> operator [C++], comparing specific objects'
- operator< [C++], bstr
- == operator [C++], with specific Visual C++ objects
- operator>= [C++], bstr
- operator < [C++], bstr
- operator > [C++], bstr
ms.assetid: e153da72-37c3-4d8a-b8eb-730d65da64dd
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 474485258c69f55c957cbdde43900965f1e99c9d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [_bstr_t 類別](../cpp/bstr-t-class.md)