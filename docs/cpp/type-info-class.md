---
title: type_info 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- type_info
dev_langs:
- C++
helpviewer_keywords:
- class type_info
- type_info class
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54e4f4a2ac9be9dc68320e5121bc86e5a4280807
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941037"
---
# <a name="typeinfo-class"></a>type_info 類別
`type_info`類別描述在程式內，編譯器所產生的型別資訊。 這個類別的物件會實際儲存類型的名稱指標。 `type_info`類別也會儲存編碼的值適用於比較是否相等的兩種類型，或其排序順序。 類型的編碼規則和排序法則不會指定，而且在不同的程式之間也會有所差異。  
  
 `<typeinfo>`標頭檔必須包含才能使用`type_info`類別。 介面`type_info`類別是：  
  
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
  
 您無法具現化的物件`type_info`類別，因為類別只有 private 複製建構函式。 建構 （暫存） 的唯一辦法`type_info`物件是使用[typeid](../cpp/typeid-operator.md)運算子。 因為指派運算子也是私人的您無法複製或指派類別的物件`type_info`。  
  
 `type_info::hash_code` 定義適用於類型的值對應的雜湊函式`typeinfo`到索引值的分佈。  
  
 運算子`==`並`!=`可以用來與其他比較是否相等和不等比較`type_info`物件，分別。  
  
 類型的排序順序和繼承關係之間並無連結。 使用`type_info::before`成員函式，來判斷型別的定序序列。 不保證，`type_info::before`會產生不同的程式或甚至執行相同程式的相同的結果。 如此一來，在`type_info::before`類似於位址的`(&)`運算子。  
  
 `type_info::name`成員函式傳回`const char*`以 null 終止的字串，表示型別的人類看得懂的名稱。 所指向的記憶體會加以快取，且絕不可直接取消配置。  
  
 `type_info::raw_name`成員函式傳回`const char*`以 null 終止的字串，代表物件類型的裝飾的名稱。 這個名稱實際上是以其裝飾形式儲存，以節省空間。 因此，此函式的速度比`type_info::name`因為它不需要解除名稱裝飾。 所傳回的字串`type_info::raw_name`函式是在比較作業中很有用，但不是可讀取。 如果您需要人類看得懂的字串，使用`type_info::name`函式。  
  
 多型類別才會產生類型資訊[/GR （啟用執行階段類型資訊）](../build/reference/gr-enable-run-time-type-information.md)指定編譯器選項。  
  
## <a name="see-also"></a>另請參閱  
 [執行階段類型資訊](../cpp/run-time-type-information.md)
