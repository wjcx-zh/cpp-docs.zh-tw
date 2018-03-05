---
title: "type_info 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- type_info
dev_langs:
- C++
helpviewer_keywords:
- class type_info
- type_info class
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9cd5a1844bfeec798ee25a3cb8e65efd019e65e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="typeinfo-class"></a>type_info 類別
**Type_info**類別描述編譯器所產生的程式中的型別資訊。 這個類別的物件會實際儲存類型的名稱指標。 **Type_info**類別也會儲存編碼的值，適用於比較是否相等的兩個型別或其排序順序。 類型的編碼規則和排序法則不會指定，而且在不同的程式之間也會有所差異。  
  
 `<typeinfo>`標頭檔必須包含才能使用**type_info**類別。 介面**type_info**類別是：  
  
```cpp
class type_info {  
public:  
    virtual ~type_info();  
    size_t hash_code() const  
    _CRTIMP_PURE bool operator==(const type_info& rhs) const;  
    _CRTIMP_PURE bool operator!=(const type_info& rhs) const;  
    _CRTIMP_PURE int before(const type_info& rhs) const;  
    _CRTIMP_PURE const char* name() const;  
    _CRTIMP_PURE const char* raw_name() const;  
};  
```  
  
 您無法具現化的物件**type_info**類別直接管理，因為類別只有 private 複製建構函式。 唯一的方式來建構 （暫存） **type_info**物件是使用[typeid](../cpp/typeid-operator.md)運算子。 指派運算子也是私人的因為您無法複製或類別的物件指派**type_info**。  
  
 **type_info:: hash_code**定義適用於對應的型別值的雜湊函式**typeinfo**索引值的分佈。  
  
 運算子`==`和`!=`可以用來與其他相等和不等比較**type_info**分別物件。  
  
 類型的排序順序和繼承關係之間並無連結。 使用**type_info**成員函式來判斷定序順序的型別。 不保證， **type_info**都會產生不同的程式或甚至執行相同程式中相同的結果。 這種方式， **type_info**類似於位址的**(&)**運算子。  
  
 **Type_info:: name**成員函式傳回**const char\*** 以 null 終止的字串代表人類看得懂的型別名稱。 所指向的記憶體會加以快取，且絕不可直接取消配置。  
  
 **Type_info:: raw_name**成員函式傳回**const char\*** 以 null 終止的字串表示裝飾的名稱的物件類型。 這個名稱實際上是以其裝飾形式儲存，以節省空間。 因此，此函式的速度比**type_info:: name**因為它不需要快速的名稱。 所傳回的字串**type_info:: raw_name**函式是在比較作業中很有用，但不是可讀取。 如果您需要人類看得懂的字串，使用**type_info:: name**函式。  
  
 多型類別才會產生型別資訊[/GR （啟用執行階段類型資訊）](../build/reference/gr-enable-run-time-type-information.md)編譯器選項已指定。  
  
## <a name="see-also"></a>請參閱  
 [執行階段類型資訊](../cpp/run-time-type-information.md)
