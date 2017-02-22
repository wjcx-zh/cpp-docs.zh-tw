---
title: "type_info 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "type_info"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "類別 type_info"
  - "type_info 類別"
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# type_info 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**type\_info** 類別會描述編譯器在程式內產生的類型資訊。  這個類別的物件會實際儲存類型的名稱指標。  **type\_info** 類別也會儲存編碼值，適用於比較兩個類型是否相等或其排序順序。  類型的編碼規則和排序法則不會指定，而且在不同的程式之間也會有所差異。  
  
 其中必須包含 \<`typeinfo>` 標頭檔，才能使用 **type\_info** 類別。  **type\_info** 類別的介面為：  
  
```  
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
  
 由於 **type\_info** 類別只有 private 複製建構函式，因此無法直接具現化該類別的物件。  建構 \(暫存\) **type\_info** 物件的唯一方式是使用 [typeid](../cpp/typeid-operator.md) 運算子。  由於指派運算子也屬於 private，因此您無法複製或指派 **type\_info** 類別的物件。  
  
 **type\_info::hash\_code** 會定義雜湊函式，適用於將 **typeinfo** 類型的值對應至散佈的索引值。  
  
 運算子 `==` 和 `!=` 可分別用於與其他 **type\_info** 物件進行相等和不等比較。  
  
 類型的排序順序和繼承關係之間並無連結。  使用 **type\_info::before** 成員函式可判斷類型的排序法則。  不過並不保證 **type\_info::before** 在不同的程式中，甚至執行相同程式的次數不同時，都會產生相同的結果。  從這方面來看，**type\_info::before** 類似傳址 **\(&\)** 運算子。  
  
 **type\_info::name** 成員函式會將 **const char\*** 傳回至以 null 終止的字串，該字串代表人類看得懂的類型名稱。  所指向的記憶體會加以快取，且絕不可直接取消配置。  
  
 **type\_info::raw\_name** 成員函式會將 **const char\*** 傳回至以 null 終止的字串，該字串代表物件類型的裝飾名稱。  這個名稱實際上是以其裝飾形式儲存，以節省空間。  因此，這個函式比 **type\_info::name** 快速，因為它不需要解除名稱裝飾。  雖然 **type\_info::raw\_name** 函式所傳回的字串在比較運算時很有用，但是無法閱讀。  如果您需要人類看得懂的字串，請改用 **type\_info::name** 函式。  
  
 只有在指定 [\/GR \(啟用執行階段類型資訊\)](../build/reference/gr-enable-run-time-type-information.md) 編譯器選項時，才會產生多型類別的類型資訊。  
  
## 請參閱  
 [執行階段類型資訊](../cpp/run-time-type-information.md)