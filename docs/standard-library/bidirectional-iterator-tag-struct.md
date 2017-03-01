---
title: "bidirectional_iterator_tag 結構 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xutility/std::bidirectional_iterator_tag
- std::bidirectional_iterator_tag
- std.bidirectional_iterator_tag
- bidirectional_iterator_tag
dev_langs:
- C++
helpviewer_keywords:
- bidirectional_iterator_tag class
- bidirectional_iterator_tag struct
ms.assetid: 9ac06066-b8ae-44b6-bee4-b05855f6a31a
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
ms.openlocfilehash: 33302a822cc36adf7f68d7cce29b678654aabb29
ms.lasthandoff: 02/24/2017

---
# <a name="bidirectionaliteratortag-struct"></a>bidirectional_iterator_tag 結構
類別，為表示雙向迭代器的 **iterator_category** 函式提供傳回型別。  
  
## <a name="syntax"></a>語法  
  
```
struct bidirectional_iterator_tag    : public forward_iterator_tag {};
```  
  
## <a name="remarks"></a>備註  
 分類標籤類別會用作演算法選擇的編譯標籤。 樣板函式必須尋找其迭代器引數最精確的分類，如此一來在編譯時間就可以使用最有效率的演算法。 對於 `Iterator` 類型的每個迭代器，必須將 `iterator_traits`< `Iterator`>:: **iterator_category** 定義為描述迭代器行為最精確的分類標籤。  
  
 當 **Iter** 描述的物件可當作雙向迭代器時，此類型與 **iterator**\< **Iter**>:: **iterator_category** 相同。  
  
## <a name="example"></a>範例  
 如需如何使用 `bidirectional_iterator_tag` 的範例，請參閱 [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<iterator>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [forward_iterator_tag 結構](../standard-library/forward-iterator-tag-struct.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)




