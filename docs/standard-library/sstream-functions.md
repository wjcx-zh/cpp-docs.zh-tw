---
title: "&lt;sstream&gt; 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- sstream/std::swap
ms.assetid: bc9607e8-7c6b-44ef-949b-19e917b450ad
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: 1c186910203df481bef047f2d1813097590c7508
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ltsstreamgt-functions"></a>&lt;sstream&gt; 函式
||  
|-|  
|[swap](#sstream_swap)|  
  
##  <a name="sstream_swap"></a> swap  
 在 `sstream` 物件之間交換值。  
  
```  
template <class Elem, class Tr, class Alloc>  
void swap(
    basic_stringbuf<Elem, Tr, Alloc>& left,  
    basic_stringbuf<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>  
void swap(
    basic_istringstream<Elem, Tr, Alloc>& left,  
    basic_istringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>  
void swap(
    basic_ostringstream<Elem, Tr, Alloc>& left,  
    basic_ostringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>  
void swap(
    basic_stringstream<Elem, Tr, Alloc>& left,  
    basic_stringstream<Elem, Tr, Alloc>& right);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`left`|`sstream` 物件的參考。|  
|`right`|`sstream` 物件的參考。|  
  
### <a name="remarks"></a>備註  
 這個範本函式會執行 `left.swap(right)`。  
  
## <a name="see-also"></a>請參閱  
 [\<sstream>](../standard-library/sstream.md)

