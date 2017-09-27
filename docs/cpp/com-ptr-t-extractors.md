---
title: "_com_ptr_t 擷取器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::operatorInterface&
- operatorInterface*
- operatorInterface&
- _com_ptr_t::operatorbool
- _com_ptr_t.operator->
- _com_ptr_t.operator*
- _com_ptr_t::operator->
- _com_ptr_t::operator*
- _com_ptr_t.operatorInterface&
- _com_ptr_t.operatorbool
dev_langs:
- C++
helpviewer_keywords:
- operator Interface&
- '* operator, with specific objects'
- operator&
- operator*
- -> operator, with specific objects
- '& operator, with specific objects'
- operator Interface*
- operator *
- operator->
- operator bool
- extractors, _com_ptr_t class
- extractors
ms.assetid: 194b9e0e-123c-49ff-a187-0a7fcd68145a
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
ms.openlocfilehash: 136afa55361ff25f9ad606886be938a00551393d
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="comptrt-extractors"></a>_com_ptr_t 擷取器
**Microsoft 特定的**  
  
 擷取封裝的 COM 介面指標。  
  
## <a name="syntax"></a>語法  
  
```  
  
      operator Interface*( ) const throw( );   
operator Interface&( ) const;   
Interface& operator*( ) const;   
Interface* operator->( ) const;   
Interface** operator&( ) throw( );   
operator bool( ) const throw( );  
```  
  
## <a name="remarks"></a>備註  
  
-   **operator Interface&\* **傳回封裝的介面指標，這可能是**NULL**。  
  
-   **operator Interface& &**將參考傳回給封裝的介面指標，並會發出錯誤，如果指標位於**NULL**。  
  
-   **運算子\***可讓智慧型指標物件作用就如同實際封裝的介面取值時一樣。  
  
-   **operator->**可讓智慧型指標物件作用就如同實際封裝的介面取值時一樣。  
  
-   **運算子 （& s)**釋放任何封裝的介面指標，它與取代**NULL**，並傳回封裝的指標的位址。 這可讓智慧型指標的位址傳遞至函式具有**出**透過它傳回介面指標的參數。  
  
-   **運算子 bool**允許條件運算式中使用智慧型指標物件。 這個運算子會傳回**true**如果指標不是**NULL**。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_ptr_t 類別](../cpp/com-ptr-t-class.md)
