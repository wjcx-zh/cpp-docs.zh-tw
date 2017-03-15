---
title: '&lt;functional&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <functional>
- functional/std::<functional>
- std::<functional>
dev_langs:
- C++
helpviewer_keywords:
- functors
- functional header
ms.assetid: 7dd463e8-a29f-49bc-aedd-8fa53b54bfbc
caps.latest.revision: 27
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
ms.sourcegitcommit: 41b445ceeeb1f37ee9873cb55f62d30d480d8718
ms.openlocfilehash: dcac506c06aac3c29ba2251af4281a713eec7491
ms.lasthandoff: 02/24/2017

---
# <a name="ltfunctionalgt"></a>&lt;functional&gt;
定義可協助建構「函式物件」(又稱為函子 (Functor)) 及其繫結器的「C++ 標準程式庫」函式。 函式物件是定義 `operator()` 的類型物件。 函式物件可以是函式指標，不過該物件更常用來儲存可在函式呼叫期間存取的其他資訊。  
  
## <a name="syntax"></a>語法  
  
```  
#include <functional>  
```  
  
## <a name="remarks"></a>備註  
 演算法需要兩種類型的函式物件：一元和二元。 一元函式物件需要一個引數，而二元函式物件需要兩個引數。 函式物件和函式指標都可當作述詞來傳遞給演算法，但函式物件還具有可調適性，因此能增加「C++ 標準程式庫」的範圍、彈性及效率。 例如，如果值需要在傳遞給演算法之前繫結至函式，則無法使用函式指標。 函式配接器會將函式指標轉換成可繫結至值的可調適性函式物件。 \<functional> 標頭也包含成員函式配接器，可允許將成員函式當作可調適性函式物件來呼叫。 如果函式具有指定其引數和傳回型別的巢狀類型宣告，則具有可調適性。 C++ 標準要求這個可調適性的實作方式，必須是讓所有標準物件類別都繼承自 unary_function 或 binary_function 基底類別。 函式物件及其配接器可讓「C++ 標準程式庫」升級現有的應用程式，並協助將程式庫整合到 C++ 程式設計環境中。  
  
 \<functional> 中函式物件的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 實作包含「透明運算子函子」(Transparent Operator Functor)，這是標準函式物件的特製化，不接受任何範本參數，而且可將函式引數完整轉送並將結果完整傳回。 這項功能是 C++14 草稿標準規格的一部分。 當您叫用算術、比較、邏輯和位元運算子函子時，這些樣板特製化不會要求您指定引數類型。 您可以針對自己所擁有的類型或類型的異質組合，多載算術、比較、邏輯或位元運算子，然後使用透明運算子函子做為函式引數。 例如，如果您的 *MyType* 類型實作 `operator<`，則您可以呼叫 `sort(my_collection.begin(), my_collection.end(), less<>())`，而不是明確指定 `sort(my_collection.begin(), my_collection.end(), less<MyType>())` 類型。  
  
## <a name="c11c14-implementation"></a>C++11/C++14 實作  
 C++11/C++14 的 Visual C++ 實作中已新增下列功能：  
  
-   「呼叫簽章」(Call Signature) 是傳回類型的名稱，後面會接著以括號括住、內含零個或多個引數類型的逗號分隔清單。  
  
-   「可呼叫類型」(Callable Type) 是函式指標、成員函式指標、成員資料指標，或其物件緊接在函式呼叫運算子左側的類別類型。  
  
-   「可呼叫物件」(Callable Object) 是屬於可呼叫類型的物件。  
  
-   「呼叫包裝函式類型」(Call Wrapper Type) 是包含可呼叫物件並支援轉送至該物件之呼叫作業的類型。  
  
-   「呼叫包裝函式」(Call Wrapper) 是屬於呼叫包裝函式類型的物件。  
  
-   「目標物件」(Target Object) 是呼叫包裝函式物件所持有的可呼叫物件。  
  
 虛擬函式 `INVOKE(f, t1, t2, ..., tN)` 表示下列其中一項：  
  
- `(t1.*f)(t2, ..., tN)`：當 `f` 是 `T` 類別的成員函式指標，而且 `t1` 是 `T` 類型的物件、`T` 類型的物件參考或衍生自 `T` 之類型的物件參考時。  
  
- `((*t1).*f)(t2, ..., tN)`：當 `f` 是 `T` 類別的成員函式指標，而且 `t1` 不是上一個項目所描述的任何一個類型時。  
  
- `t1.*f`：當 N == 1，`f` 是 `T` 類別的成員資料指標，而且 `t1` 是 `T` 類型的物件、`T` 類型的物件參考或衍生自 `T` 之類型的物件參考時。  
  
- `(*t1).*f`：當 N == 1，`f` 是 `T` 類別的成員資料指標，而且 `t1` 不是上一個項目所描述的任何一個類型時。  
  
- `f(t1, t2, ..., tN)`：其他所有情況。  
  
 虛擬函式 `INVOKE(f, t1, t2, ..., tN, R)` 表示 `INVOKE(f, t1, t2, ..., tN)` 會隱含地轉換成 `R`。  
  
 如果呼叫包裝函式具有「弱式結果類型」(Weak Result Type)，則其成員類型 `result_type` 的類型會根據包裝函式之目標物件的 `T` 類型，如下所示：  
  
-   如果 `T` 是函式的指標，則 `result_type` 與 `T` 的傳回類型同義。  
  
-   如果 `T` 是成員函式的指標，則 `result_type` 與 `T` 的傳回類型同義。  
  
-   如果 `T` 是具有成員類型 `result_type` 的類別類型，則 `result_type` 與 `T::result_type` 同義。  
  
-   否則沒有成員 `result_type`。  
  
 每個呼叫包裝函式具有一個移動建構函式和一個複製建構函式。 「簡單呼叫包裝函式」(Simple Call Wrapper) 是具有指派運算子的呼叫包裝函式，其中它的複製建構函式、移動建構函式及指派運算子不會擲回例外狀況。 「轉送呼叫包裝函式」(Forwarding Call Wrapper) 是可藉由使用任意引數清單來呼叫的呼叫包裝函式，而且它可將引數當作參考傳遞給已包裝的可呼叫物件。 所有右值引數都會做為右值參考傳遞，而左值引數會做為左值參考傳遞。  
  
### <a name="classes"></a>類別  
  
|||  
|-|-|  
|[bad_function_call](../standard-library/bad-function-call-class.md)|描述所擲回之例外狀況的類別，這個例外狀況會指出對 [function](../standard-library/function-class.md) 物件上的 `operator()` 呼叫失敗，因為物件是空的。|  
|[binary_negate](../standard-library/binary-negate-class.md)|提供一個成員函式的樣板類別，這個成員函式可將指定二元函式的傳回值變成負值。|  
|[binder1st](../standard-library/binder1st-class.md)|提供一個建構函式的樣板類別，這個建構函式透過將二元函式的第一個引數繫結至指定值，將二元函式物件轉換成一元函式物件。|  
|[binder2nd](../standard-library/binder2nd-class.md)|提供一個建構函式的樣板類別，這個建構函式透過將二元函式的第二個引數繫結至指定值，將二元函式物件轉換成一元函式物件。|  
|[const_mem_fun_ref_t](../standard-library/const-mem-fun-ref-t-class.md)|配接器類別，這個類別允許不接受引數的常數成員函式在使用參考引數初始化時，可當做一元函式物件來呼叫。|  
|[const_mem_fun_t](../standard-library/const-mem-fun-t-class.md)|配接器類別，這個類別允許不接受引數的常數成員函式在使用指標引數初始化時，可當做一元函式物件來呼叫。|  
|[const_mem_fun1_ref_t](../standard-library/const-mem-fun1-ref-t-class.md)|配接器類別，這個類別允許不接受單一引數的常數成員函式在使用參考引數初始化時，可當做二元函式物件來呼叫。|  
|[const_mem_fun1_t](../standard-library/const-mem-fun1-t-class.md)|配接器類別，這個類別允許不接受單一引數的常數成員函式在使用指標引數初始化時，可當做二元函式物件來呼叫。|  
|[function](../standard-library/function-class.md)|包裝可呼叫物件的類別。|  
|[hash](../standard-library/hash-class.md)|此類別可以計算值的雜湊碼。|  
|[is_bind_expression](../standard-library/is-bind-expression-class.md)|此類別測試呼叫 `bind` 時是否產生特定類型。|  
|[is_placeholder](../standard-library/is-placeholder-class.md)|此類別測試特定類型是否為預留位置。|  
|[mem_fun_ref_t](../standard-library/mem-fun-ref-t-class.md)|配接器類別，可允許將不接受任何引數的 **non_const** 成員函式在以參考引數初始化時，當作一元函式物件來呼叫。|  
|[mem_fun_t](../standard-library/mem-fun-t-class.md)|配接器類別，可允許將不接受任何引數的 **non_const** 成員函式在以指標引數初始化時，當作一元函式物件來呼叫。|  
|[mem_fun1_ref_t](../standard-library/mem-fun1-ref-t-class.md)|配接器類別，可允許將接受單一引數的 **non_const** 成員函式在以參考引數初始化時，當作二元函式物件來呼叫。|  
|[mem_fun1_t](../standard-library/mem-fun1-t-class.md)|配接器類別，可允許將接受單一引數的 **non_const** 成員函式在以指標引數初始化時，當作二元函式物件來呼叫。|  
|[pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md)|將二元函式指標轉換成可調適性二元函式。|  
|[pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md)|將一元函式指標轉換成可調適性一元函式。|  
|[reference_wrapper](../standard-library/reference-wrapper-class.md)|包裝參考的類別。|  
|[unary_negate](../standard-library/unary-negate-class.md)|提供一個成員函式的樣板類別，這個成員函式可將指定一元函式的傳回值變成負值。|  
  
### <a name="functions"></a>函式  
  
|||  
|-|-|  
|[bind](../standard-library/functional-functions.md#bind_function)|將引數繫結至可呼叫物件。|  
|[bind1st](../standard-library/functional-functions.md#bind1st_function)|協助程式樣板函式，可建立配接器，透過將二元函式的第一個引數繫結至指定值，將二元函式物件轉換成一元函式物件。|  
|[bind2nd](../standard-library/functional-functions.md#bind2nd_function)|協助程式樣板函式，可建立配接器，透過將二元函式的第二個引數繫結至指定值，將二元函式物件轉換成一元函式物件。|  
|[bit_and](../standard-library/functional-functions.md#bit_and_function)|傳回兩個參數的位元邏輯 AND (二元運算子 &)。|  
|[bit_not](../standard-library/functional-functions.md#bit_not_function)|傳回參數的位元邏輯補數 (運算子 ~)。|  
|[bit_or](../standard-library/functional-functions.md#bit_or_function)|傳回兩個參數的位元邏輯 OR (運算子 &#124;)。|  
|[bit_xor](../standard-library/functional-functions.md#bit_xor_function)|傳回兩個參數的位元邏輯 XOR (運算子 ^)。|  
|[cref](../standard-library/functional-functions.md#cref_function)|從引數建構常數`reference_wrapper`。|  
|[mem_fn](../standard-library/functional-functions.md#mem_fn_function)|產生簡單呼叫包裝函式。|  
|[mem_fun](../standard-library/functional-functions.md#mem_fun_function)|協助程式樣板函式，可用來建構使用指標引數初始化時之成員函式的物件配接器。|  
|[mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref_function)|協助程式樣板函式，可用來建構使用參考引數初始化時之成員函式的物件配接器。|  
|[not1](../standard-library/functional-functions.md#not1_function)|傳回一元述詞的補數。|  
|[not2](../standard-library/functional-functions.md#not2_function)|傳回二元述詞的補數。|  
|[ptr_fun](../standard-library/functional-functions.md#ptr_fun_function)|協助程式樣板函式，可用來將一元和二元函式指標分別轉換成一元和二元可調適性函式。|  
|[ref](../standard-library/functional-functions.md#ref_function)|從引數建構 `reference_wrapper` 。|  
|[swap](../standard-library/functional-functions.md#swap_function)|交換兩個 `function` 物件。|  
  
### <a name="structs"></a>結構  
  
|||  
|-|-|  
|[binary_function](../standard-library/binary-function-struct.md)|空的基底類別，定義可繼承衍生類別並提供二元函式物件的類型。|  
|[divides](../standard-library/divides-struct.md)|這個類別會提供預先定義的函式物件，該物件會在指定實值類型的項目上執行算術除法運算。|  
|[equal_to](../standard-library/equal-to-struct.md)|二元述詞，可測試指定類型的值是否等於該類型的另一個值。|  
|[greater](../standard-library/greater-struct.md)|二元述詞，可測試指定類型的值是否大於該類型的另一個值。|  
|[greater_equal](../standard-library/greater-equal-struct.md)|二元述詞，可測試指定類型的值是否大於或等於該類型的另一個值。|  
|[less](../standard-library/less-struct.md)|二元述詞，可測試指定類型的值是否小於該類型的另一個值。|  
|[less_equal](../standard-library/less-equal-struct.md)|二元述詞，可測試指定類型的值是否小於或等於該類型的另一個值。|  
|[logical_and](../standard-library/logical-and-struct.md)|這個類別會提供預先定義的函式物件，該物件會在指定實值類型的項目上執行邏輯結合運算，並測試結果為 True 或 False。|  
|[logical_not](../standard-library/logical-not-struct.md)|這個類別會提供預先定義的函式物件，該物件會在指定實值類型的項目上執行邏輯負運算，並測試結果為 True 或 False。|  
|[logical_or](../standard-library/logical-or-struct.md)|這個類別會提供預先定義的函式物件，該物件會在指定實值類型的項目上執行邏輯分離運算，並測試結果為 True 或 False。|  
|[minus](../standard-library/minus-struct.md)|這個類別會提供預先定義的函式物件，該物件會在指定實值類型的項目上執行算術減法運算。|  
|[modulus](../standard-library/modulus-struct.md)|這個類別會提供預先定義的函式物件，該物件會在指定實值類型的項目上執行算術模數運算。|  
|[multiplies](../standard-library/multiplies-struct.md)|這個類別會提供預先定義的函式物件，該物件會在指定實值類型的項目上執行算術乘法運算。|  
|[negate](../standard-library/negate-struct.md)|這個類別會提供預先定義的函式物件，該物件會傳回項目值的負值。|  
|[not_equal_to](../standard-library/not-equal-to-struct.md)|二元述詞，可測試指定類型的值是否不等於該類型的另一個值。|  
|[plus](../standard-library/plus-struct.md)|這個類別會提供預先定義的函式物件，該物件會在指定實值類型的項目上執行算術加法運算。|  
|[unary_function](../standard-library/unary-function-struct.md)|空的基底類別，這個類別定義可能繼承自衍生類別並提供一元函式物件的類型。|  
  
### <a name="objects"></a>物件  
  
|||  
|-|-|  
|[_1.._M](../standard-library/1-object.md)|可取代引數的預留位置。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator==](../standard-library/functional-operators.md#operator_eq_eq)|不允許可呼叫物件的等號比較。|  
|[operator!=](../standard-library/functional-operators.md#operator_neq)|不允許可呼叫物件的不等比較。|  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)


