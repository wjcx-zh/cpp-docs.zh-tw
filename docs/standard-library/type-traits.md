---
title: "&lt;type_traits&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<type_traits>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "typetrait 標頭 [TR1]"
  - "type_traits"
ms.assetid: 2260b51f-8160-4c66-a82f-00b534cb60d4
caps.latest.revision: 35
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 35
---
# &lt;type_traits&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義提供給其型別引數內容的相關資訊，或產生編譯時期常數轉換類型的範本。  
  
## 語法  
  
```  
#include <type_traits>  
```  
  
## 備註  
 類別和範本 `<type_traits>` 用來支援型別推斷、 分類，以及在編譯期間，偵測型別相關的錯誤，並協助您最佳化您的一般程式碼的轉換。 這些類別和範本包含一元類型特性的描述屬性的類型，描述型別，以及修改型別屬性的轉換特性之間的關聯性的二進位類型特性。  
  
 若要支援類型特性，協助程式類別， `integral_constant`, ，定義。 它具有樣板特製化 `true_type` 和 `false_type` ，形成類型述詞的基底類別。 A *類型述詞* 是採用一或多個類型引數的範本。 當類型述詞*「具有 True」*\(Hold True\) 時，會直接或間接地公開衍生自 [true\_type](../Topic/true_type%20Typedef.md)。 當類型述詞*「具有 False」*\(Hold False\) 時，會直接或間接地公開衍生自 [false\_type](../Topic/false_type%20Typedef.md)。  
  
 A *型別修飾詞* 或 *轉換特性* 是採用一或多個範本引數的範本，且具有一個成員 `type`, ，這是已修改的類型的同義字。  
  
### 別名範本  
 若要簡化型別特性運算式， [別名樣板](../cpp/aliases-and-typedefs-cpp.md) 的 `typename some_trait<T>::type` 提供，其中" `some_trait`"是範本類別名稱。 例如， [add\_const](../standard-library/add-const-class.md) 具有型別的別名樣板 `add_const_t`, ，定義為︰  
  
```cpp  
template<class T>  
    using add_const_t = typename add_const<T>::type;  
```  
  
|||||  
|-|-|-|-|  
|add\_const\_t|aligned\_storage\_t|make\_signed\_t|remove\_pointer\_t|  
|add\_cv\_t|aligned\_union\_t|make\_unsigned\_t|remove\_reference\_t|  
|add\_lvalue\_reference\_t|common\_type\_t|remove\_all\_extents\_t|remove\_volatile\_t|  
|add\_pointer\_t|conditional\_t|remove\_const\_t|result\_of\_t|  
|add\_rvalue\_reference\_t|decay\_t|remove\_cv\_t|underlying\_type\_t|  
|add\_volatile\_t|enable\_if\_t|remove\_extent\_t||  
  
### 類別  
 協助程式類別和 typedef  
  
|||  
|-|-|  
|[integral\_constant](../standard-library/integral-constant-class-bool-constant-class.md)|從類型及值建立整數常數。|  
|[true\_type](../Topic/true_type%20Typedef.md)|存有具有 True 值的整數常數。|  
|[false\_type](../Topic/false_type%20Typedef.md)|存有具有 False 值的整數常數。|  
  
 主要的型別類別  
  
|||  
|-|-|  
|[is\_void](../standard-library/is-void-class.md)|測試類型是否為 `void`。|  
|[is\_null\_pointer](../standard-library/is-null-pointer-class.md)|測試類型是否為 `std::nullptr_t`。|  
|[is\_integral](../standard-library/is-integral-class.md)|測試類型是否為整數。|  
|[is\_floating\_point](../standard-library/is-floating-point-class.md)|測試類型是否為浮點。|  
|[is\_array](../standard-library/is-array-class.md)|測試類型是否為陣列。|  
|[is\_pointer](../standard-library/is-pointer-class.md)|測試類型是否為指標。|  
|[is\_lvalue\_reference](../standard-library/is-lvalue-reference-class.md)|測試類型是否為 lvalue 參考。|  
|[is\_rvalue\_reference](../standard-library/is-rvalue-reference-class.md)|測試類型是否為 rvalue 參考。|  
|[is\_member\_object\_pointer](../standard-library/is-member-object-pointer-class.md)|測試類型是否為成員物件的指標。|  
|[is\_member\_function\_pointer](../standard-library/is-member-function-pointer-class.md)|測試類型是否為成員函式的指標。|  
|[is\_enum](../standard-library/is-enum-class.md)|測試類型是否為列舉。|  
|[is\_union](../standard-library/is-union-class.md)|測試類型是否為等位。|  
|[is\_class](../standard-library/is-class-class.md)|測試類型是否為類別。|  
|[is\_function](../standard-library/is-function-class.md)|測試類型是否為函式類型。|  
  
 複合類型類別目錄  
  
|||  
|-|-|  
|[is\_reference](../standard-library/is-reference-class.md)|測試類型是否為參考。|  
|[is\_arithmetic](../standard-library/is-arithmetic-class.md)|測試類型是否為算術。|  
|[is\_fundamental](../standard-library/is-fundamental-class.md)|測試類型是否為 `void` 或算術。|  
|[is\_object](../standard-library/is-object-class.md)|測試類型是否為物件類型。|  
|[is\_scalar](../standard-library/is-scalar-class.md)|測試類型是否為純量。|  
|[is\_compound](../standard-library/is-compound-class.md)|測試類型是否不是純量。|  
|[is\_member\_pointer](../standard-library/is-member-pointer-class.md)|測試類型是否為成員的指標。|  
  
 類型屬性  
  
|||  
|-|-|  
|[is\_const](../standard-library/is-const-class.md)|測試類型是否為 `const`。|  
|[is\_volatile](../standard-library/is-volatile-class.md)|測試類型是否為 `volatile`。|  
|[is\_trivial](../standard-library/is-trivial-class.md)|測試類型是否為一般。|  
|[is\_trivially\_copyable](../standard-library/is-trivially-copyable-class.md)|測試類型是否為可完整複製。|  
|[is\_standard\_layout](../standard-library/is-standard-layout-class.md)|輸入測試類型是否為標準配置。|  
|[is\_pod](../standard-library/is-pod-class.md)|測試類型是否為 POD。|  
|[is\_literal\_type](../standard-library/is-literal-type-class.md)|測試是否能夠類型 `constexpr` 變數或用於 `constexpr` 函式。|  
|[is\_empty](../standard-library/is-empty-class.md)|測試類型是否為空的類別。|  
|[is\_polymorphic](../standard-library/is-polymorphic-class.md)|測試類型是否為多型類別。|  
|[is\_abstract](../standard-library/is-abstract-class.md)|測試類型是否有抽象類別。|  
|[is\_final](../standard-library/is-final-class.md)|測試類型是否為類別型別標示為 `final`。|  
|[is\_signed](../standard-library/is-signed-class.md)|測試類型是否為有正負號整數。|  
|[is\_unsigned](../standard-library/is-unsigned-class.md)|測試類型是否為無正負號整數。|  
|[is\_constructible](../standard-library/is-constructible-class.md)|測試類型是否為可使用指定的引數型別。|  
|[is\_default\_constructible](../standard-library/is-default-constructible-class.md)|測試類型是否有預設建構函式。|  
|[is\_copy\_constructible](../standard-library/is-copy-constructible-class.md)|測試類型是否有複製建構函式。|  
|[is\_move\_constructible](../standard-library/is-move-constructible-class.md)|測試類型是否有移動建構函式。|  
|[is\_assignable](../standard-library/is-assignable-class.md)|測試第一個型別是否可以指派第二個類型的值。|  
|[is\_copy\_assignable](../standard-library/is-copy-assignable-class.md)|測試是否為型別可以指派 const 參考值的型別。|  
|[is\_move\_assignable](../standard-library/is-move-assignable-class.md)|測試是否為型別可以指派類型的右值參考。|  
|[is\_destructible](../standard-library/is-destructible-class.md)|測試類型是否為易損壞的。|  
|[is\_trivially\_constructible](../standard-library/is-trivially-constructible-class.md)|測試是否不使用任何非一般的作業時使用指定的型別建構的類型。|  
|[is\_trivially\_default\_constructible](../standard-library/is-trivially-default-constructible-class.md)|測試是否不使用任何非一般的作業類型預設建構時。|  
|[is\_trivially\_copy\_constructible](../standard-library/is-trivially-copy-constructible-class.md)|測試是否不使用任何非一般的作業類型複製建構時。|  
|[is\_trivially\_move\_constructible](../standard-library/is-trivially-move-constructible-class.md)|測試是否不使用任何非一般的作業類型時移動建構。|  
|[is\_trivially\_assignable](../standard-library/is-trivially-assignable-class.md)|測試是否類型可指派作業會不使用任何非一般的作業。|  
|[is\_trivially\_copy\_assignable](../standard-library/is-trivially-copy-assignable-class.md)|測試類型是否可以指派的複製和指派會使用任何非一般的作業。|  
|[is\_trivially\_move\_assignable](../standard-library/is-trivially-move-assignable-class.md)|測試類型是否可以指派的移動和指派會使用任何非一般的作業。|  
|[is\_trivially\_destructible](../standard-library/is-trivially-destructible-class.md)|測試是否的型別是可破壞解構函式會不使用任何非一般的作業。|  
|[is\_nothrow\_constructible](../standard-library/is-nothrow-constructible-class.md)|測試是否型別建構已知不使用指定的型別建構時擲回。|  
|[is\_nothrow\_default\_constructible](../standard-library/is-nothrow-default-constructible-class.md)|測試類型是否為預設的建構和已知不預設建構時擲回。|  
|[is\_nothrow\_copy\_constructible](../standard-library/is-nothrow-copy-constructible-class.md)|測試是否型別是開放式的複本，不知道複製建構函式擲回。|  
|[is\_nothrow\_move\_constructible](../standard-library/is-nothrow-move-constructible-class.md)|測試是否型別是開放式的移動，不知道移動建構函式擲回。|  
|[is\_nothrow\_assignable](../standard-library/is-nothrow-assignable-class.md)|測試是否的型別是可指派使用指定的型別指派已知不會擲回。|  
|[is\_nothrow\_copy\_assignable](../standard-library/is-nothrow-copy-assignable-class.md)|測試是否型別是可指派的複本，不知道作業擲回。|  
|[is\_nothrow\_move\_assignable](../standard-library/is-nothrow-move-assignable-class.md)|測試是否型別是可指派的移動作業已知不會擲回。|  
|[is\_nothrow\_destructible](../standard-library/is-nothrow-destructible-class.md)|測試是否類型是可破壞，而不知道解構函式擲回。|  
|[has\_virtual\_destructor](http://msdn.microsoft.com/zh-tw/c0f85f0b-c63c-410d-a046-72eeaf44f7eb)|測試類型是否有虛擬解構函式。|  
  
 型別屬性的查詢  
  
|||  
|-|-|  
|[alignment\_of](../standard-library/alignment-of-class.md)|取得類型的對齊方式。|  
|[rank](../standard-library/rank-class.md)|取得陣列維度的數目。|  
|[extent](../standard-library/extent-class.md)|取得指定的陣列維度中的項目數目。|  
  
 類型關聯  
  
|||  
|-|-|  
|[is\_same](../standard-library/is-same-class.md)|測試兩個類型是否一樣。|  
|[is\_base\_of](../standard-library/is-base-of-class.md)|測試是否為基底的另一個類型。|  
|[is\_convertible](../standard-library/is-convertible-class.md)|測試某個類型是否可轉換為另一個類型。|  
  
 Const volatile 修改  
  
|||  
|-|-|  
|[add\_const](../standard-library/add-const-class.md)|會產生 `const` 從型別類型。|  
|[add\_volatile](../standard-library/add-volatile-class.md)|會產生 `volatile` 從型別類型。|  
|[add\_cv](../standard-library/add-cv-class.md)|會產生 `const``volatile` 從型別類型。|  
|[remove\_const](../standard-library/remove-const-class.md)|會產生類型的非常數類型。|  
|[remove\_volatile](../standard-library/remove-volatile-class.md)|會產生類型的非暫時性類型。|  
|[remove\_cv](../standard-library/remove-cv-class.md)|會產生類型的非 const 靜態類型。|  
  
 參考的修改  
  
|||  
|-|-|  
|[add\_lvalue\_reference](../standard-library/add-lvalue-reference-class.md)|會產生型別從型別參考。|  
|[add\_rvalue\_reference](../standard-library/add-rvalue-reference-class.md)|會產生從型別為右值參考|  
|[remove\_reference](../standard-library/remove-reference-class.md)|會產生類型的非參考類型。|  
  
 符號修改  
  
|||  
|-|-|  
|[make\_signed](../standard-library/make-signed-class.md)|產生的型別，如果簽章或最小帶正負號型別大於或等於大小輸入。|  
|[make\_unsigned](../standard-library/make-unsigned-class.md)|產生的型別，如果不帶正負號或最小不帶正負號型別大於或等於大小輸入。|  
  
 陣列的修改  
  
|||  
|-|-|  
|[remove\_all\_extents](../standard-library/remove-all-extents-class.md)|產生非陣列類型的陣列型別。|  
|[remove\_extent](../standard-library/remove-extent-class.md)|會產生從陣列類型的元素型別。|  
  
 指標的修改  
  
|||  
|-|-|  
|[add\_pointer](../standard-library/add-pointer-class.md)|會產生從型別類型的指標。|  
|[remove\_pointer](../standard-library/remove-pointer-class.md)|產生的指標類型的類型。|  
  
 其他轉換  
  
|||  
|-|-|  
|[aligned\_storage](../standard-library/aligned-storage-class.md)|為對齊類型配置未初始化的記憶體。|  
|[aligned\_union](../standard-library/aligned-union-class.md)|使用非簡單式建構函式或解構函式為對齊的聯集配置未初始化的記憶體。|  
|[common\_type](../standard-library/common-type-class.md)|產生的參數組件的所有類型的一般型別。|  
|[conditional](../standard-library/conditional-class.md)|如果條件為 true，就會產生第一個指定的型別，否則為第二個指定的型別。|  
|[decay](../standard-library/decay-class.md)|傳值方式傳遞時，會產生型別。 建立非參考、非常數或非暫時性的類型，或建立類型的指標。|  
|[enable\_if](../standard-library/enable-if-class.md)|如果條件為 true，就會產生指定的型別，否則沒有型別。|  
|[result\_of](../standard-library/result-of-class1.md)|決定傳回的型別之型別的可呼叫使用指定的引數類型。|  
|[underlying\_type](../standard-library/underlying-type-class.md)|產生的列舉型別為基礎的整數型別。|  
  
## 請參閱  
 [\<functional\>](../standard-library/functional.md)