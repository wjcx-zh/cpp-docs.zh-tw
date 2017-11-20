---
title: "alignment_of 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::alignment_of
dev_langs: C++
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2e20d01c50ea743f62c1cca9e45eedd86a5d4b8c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="alignmentof-class"></a>alignment_of 類別
取得指定類型的對齊方式。 此結構是針對 [alignof](../cpp/alignof-and-alignas-cpp.md) 所實作。 若只需要查詢對齊值，請直接使用 `alignof`。 當您需要整數常數 (例如進行標記分派時)，請使用 alignment_of。  
  
## <a name="syntax"></a>語法  
  
```
template <class Ty>
struct alignment_of;
```  
  
#### <a name="parameters"></a>參數  
 `Ty`  
 要查詢的類型。  
  
## <a name="remarks"></a>備註  
 類型查詢會保存類型 `Ty` 的對齊值。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)   
 [aligned_storage 類別](../standard-library/aligned-storage-class.md)
