---
title: _com_ptr_t 關係運算子 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::operator>
- _com_ptr_t::operator>=
- _com_ptr_t::operator<=
- _com_ptr_t::operator==
- _com_ptr_t::operator!=
- _com_ptr_t::operator<
dev_langs:
- C++
helpviewer_keywords:
- '>= operator [C++], comparing specific objects'
- '!= operator'
- operator > [C++], pointers
- operator>= [C++], pointers
- operator < [C++], pointers
- operator!= [C++], relational operators
- < operator [C++], comparing specific objects
- operator== [C++], pointers
- operator == [C++], pointers
- <= operator [C++], with specific objects
- relational operators [C++], _com_ptr_t class
- operator >= [C++], pointers
- operator != [C++], relational operators
- operator <= [C++], pointers
- '> operator [C++], comparing specific objects'
- operator<= [C++], pointers
- operator< [C++], pointers
- == operator [C++], with specific Visual C++ objects
ms.assetid: 5ae4028c-33ee-485d-bbda-88d2604d6d4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 411e1649b8d9a7f072af48103ff17af92e1a7deb
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942998"
---
# <a name="comptrt-relational-operators"></a>_com_ptr_t 關係運算子
**Microsoft 專屬**  
  
 比較智慧型指標物件與另一個智慧型指標、 一般介面指標，或為 NULL。  
  
## <a name="syntax"></a>語法  
  
```  
  
template<typename _OtherIID>   
bool operator==( const _com_ptr_t<_OtherIID>& p );  
  
template<typename _OtherIID>    
bool operator==( _com_ptr_t<_OtherIID>& p );  
  
template<typename _InterfaceType>   
bool operator==( _InterfaceType* p );  
  
template<>   
bool operator==( Interface* p );  
  
template<>   
bool operator==( const _com_ptr_t& p ) throw();  
  
template<>   
bool operator==( _com_ptr_t& p ) throw();  
  
bool operator==( Int null );  
  
template<typename _OtherIID>   
bool operator!=( const _com_ptr_t<_OtherIID>& p );  
  
template<typename _OtherIID>   
bool operator!=( _com_ptr_t<_OtherIID>& p );  
  
template<typename _InterfaceType>   
bool operator!=( _InterfaceType* p );  
  
bool operator!=( Int null );  

template<typename _OtherIID>   
bool operator<( const _com_ptr_t<_OtherIID>& p );  
  
template<typename _OtherIID>   
bool operator<( _com_ptr_t<_OtherIID>& p );  
  
template<typename _InterfaceType>   
bool operator<( _InterfaceType* p );  

template<typename _OtherIID>   
bool operator>( const _com_ptr_t<_OtherIID>& p );  
  
template<typename _OtherIID>   
bool operator>(_com_ptr_t< _OtherIID>& p );  
  
template<typename _InterfaceType>   
bool operator>( _InterfaceType* p );  
  
template<typename _OtherIID>   
bool operator<=( const _com_ptr_t<_OtherIID>& p );  
  
template<typename _OtherIID>   
bool operator<=( _com_ptr_t<_OtherIID>& p );  
  
template<typename _InterfaceType>   
bool operator<=( _InterfaceType* p );  
  
template<typename _OtherIID>  
bool operator>=( const _com_ptr_t<_OtherIID>& p );  
  
template<typename _OtherIID>   
bool operator>=( _com_ptr_t<_OtherIID>& p );  
  
template<typename _InterfaceType>   
bool operator>=( _InterfaceType* p );  
```  
  
## <a name="remarks"></a>備註  
 比較的智慧型指標物件到另一個智慧型指標、 一般介面指標，或為 NULL。 除了 NULL 指標的測試，這些運算子會先查詢兩個指標`IUnknown`，並比較結果。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_com_ptr_t 類別](../cpp/com-ptr-t-class.md)