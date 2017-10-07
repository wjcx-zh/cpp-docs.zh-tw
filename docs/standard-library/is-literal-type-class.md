---
title: "is_literal_type 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::is_literal_type
dev_langs:
- C++
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: c8aca3719c6a4534f92a5bf44ad8219d9d4e3141
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="isliteraltype-class"></a>is_literal_type 類別
測試類型是否可用來作為 `constexpr` 變數，或是被 `constexpr` 函式建構、使用或傳回。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>  
struct is_literal_type;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要查詢的類型。  
  
## <a name="remarks"></a>備註  
 如果類型 `T` 是「常值類型」，類型述詞執行個體的值就會是 true，否則會是 false。 常值類型若不是 `void`、純量類型、參考類型、常值類型的陣列，就是常值類別類型。 常值類別類型是一種擁有極簡解構函式的類別類型，它若不是匯總類型，就是至少有一個非移動、非複製 `constexpr` 建構函式，且其所有基底類別和非靜態資料成員都是非揮發性的常值類型。 雖然常值的類型一律是常值類型，但常值類型的概念還包括編譯器可在編譯階段評估為 `constexpr` 的任何項目。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)




