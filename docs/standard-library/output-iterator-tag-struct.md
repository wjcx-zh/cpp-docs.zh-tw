---
title: "output_iterator_tag 結構 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xutility/std::output_iterator_tag
dev_langs: C++
helpviewer_keywords:
- output_iterator_tag class
- output_iterator_tag struct
ms.assetid: c23a4331-b069-4fa0-9c3a-1c9be7095553
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a45dd68f5788244c7d7f1ea72b22af5f96c1a0d8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="outputiteratortag-struct"></a>output_iterator_tag 結構
類別，為表示輸出迭代器的 **iterator_category** 函式提供傳回型別。  
  
## <a name="syntax"></a>語法  
  
struct output_iterator_tag {};  
  
## <a name="remarks"></a>備註  
 分類標籤類別會用來當作可供選取演算法的編譯標籤。 範本函式必須尋找其迭代器引數的最明確分類，如此它才能在編譯階段使用最有效率的演算法。 對於 `Iterator` 型別的每個迭代器，必須將 `iterator_traits`< `Iterator`> **::iterator_category** 定義為描述迭代器行為的最明確分類標籤。  
  
 當 **Iter** 描述可當作輸出迭代器的物件時，此型別與 **iterator**\< **Iter**> **::iterator_category** 相同。  
  
 如同其他的迭代器標籤，此標籤並未在迭代器的 `value_type` 或 `difference_type` 上參數化，因為輸出迭代器並不具有 `value_type` 或 `difference_type`。  
  
## <a name="example"></a>範例  
 如需如何使用 **iterator_tag** 的範例，請參閱 [iterator_traits](../standard-library/iterator-traits-struct.md) 或 [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<iterator>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)



