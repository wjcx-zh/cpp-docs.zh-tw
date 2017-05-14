---
title: "&lt;sstream&gt; 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sstream/std::swap
ms.assetid: bc9607e8-7c6b-44ef-949b-19e917b450ad
caps.latest.revision: 10
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 3b5d850026627127e539d39faca18574d72d2ff8
ms.contentlocale: zh-tw
ms.lasthandoff: 04/19/2017

---
# <a name="ltsstreamgt-functions"></a>&lt;sstream&gt; 函式
||  
|-|  
|[swap](#sstream_swap)|  
  
##  <a name="sstream_swap"></a>  swap  
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
  
|參數|說明|  
|---------------|-----------------|  
|`left`|`sstream` 物件的參考。|  
|`right`|`sstream` 物件的參考。|  
  
### <a name="remarks"></a>備註  
 樣板函式會執行 `left.swap(right)`。  
  
## <a name="see-also"></a>另請參閱  
 [\<sstream>](../standard-library/sstream.md)


