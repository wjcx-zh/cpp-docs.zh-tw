---
title: "enable_if 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- enable_if
- std::enable_if
- type_traits/std::enable_if
dev_langs:
- C++
helpviewer_keywords:
- enable_if class
- enable_if
ms.assetid: c6b8d41c-a18f-4e30-a39e-b3aa0e8fd926
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: febf80876856eb8f27ccb00310f9ceece30c2047
ms.lasthandoff: 02/24/2017

---
# <a name="enableif-class"></a>enable_if 類別
有條件地建立類型的執行個體，以進行 SFINAE 多載解析。 只有 `enable_if<Condition,Type>::type` 為 `Type` 時，才會有巢狀 typedef `Condition` (而且是 `true` 的同義字)。  
  
## <a name="syntax"></a>語法  
  
```
template <bool B, class T = void>
struct enable_if;
```  
  
#### <a name="parameters"></a>參數  
 `B`  
 判斷所產生類型是否存在的值。  
  
 `T`  
 `B` 為 true 時要具現化的類型。  
  
## <a name="remarks"></a>備註  
 如果 `B` 為 true，則 `enable_if<B, T>` 具有名稱為 "type" 的巢狀 typedef (其為 `T` 的同義字)。  
  
 如果 `B` 為 false，則 `enable_if<B, T>` 沒有名稱為 "type" 的巢狀 typedef。  
  
 會提供此別名範本：  
  
```cpp  
template <bool B, class T = void>
using enable_if_t = typename enable_if<B,T>::type;
```  
  
 在 C++ 中，範本參數的替代失敗本身並非錯誤；這稱為 *SFINAE* (替代失敗不是錯誤)。 `enable_if` 通常用來從多載解析移除候選 (亦即，它會選出多載集)，因此可能會拒絕某個定義，而使用另一個定義。 這符合 SFINAE 行為。 如需 SFINAE 的詳細資訊，請參閱 Wikipedia 上的 [Substitution failure is not an error](http://go.microsoft.com/fwlink/LinkId=394798) (替代失敗不是錯誤)。  
  
 以下是四個範例情節：  
  
-   情節 1：包裝函式的傳回類型：  
  
 ```cpp  
    template <your_stuff>  
typename enable_if<your_condition, your_return_type>::type
    yourfunction(args) {// ...
 }
// The alias template makes it more concise:
    template <your_stuff>  
enable_if_t<your_condition, your_return_type>  
yourfunction(args) {// ...
 }
```  
  
-   情節 2：加入具有預設引數的函式參數：  
  
 ```cpp  
    template <your_stuff>  
your_return_type_if_present
    yourfunction(args, enable_if_t<your condition, FOO> = BAR) {// ...
 }
```  
  
-   情節 3：加入具有預設引數的範本參數：  
  
 ```cpp  
    template <your_stuff, typename Dummy = enable_if_t<your_condition>>  
rest_of_function_declaration_goes_here
```  
  
-   情節 4：如果您的函式具有非範本引數，則可以包裝其類型：  
  
 ```cpp  
    template <typename T>  
void your_function(const T& t,
    enable_if_t<is_something<T>::value, const string&>  
s) {// ...
 }
```  
  
 情節 1 未使用建構函式和轉換運算子，因為它們沒有傳回類型。  
  
 情節 2 會將參數保持為未命名。 您可以指定 `::type Dummy = BAR`，但是名稱 `Dummy` 為無關，而賦予它名稱可能會觸發「未參考的參數」警告。 您需要選擇 `FOO` 函式參數類型和 `BAR` 預設引數。  您可以指定 `int` 和 `0`，但是您程式碼的使用者可能會因此而意外地將會遭到忽略的額外整數傳遞給函式。 建議您改用 `void **` 和 `0` 或 `nullptr`，因為幾乎沒有項目可以轉換成 `void **`：  
  
```cpp  
template <your_stuff>  
your_return_type_if_present
yourfunction(args, typename enable_if<your_condition, void **>::type = nullptr) {// ...
}
```  
  
 情節 2 也適用於一般建構函式。  不過，它不適用於轉換運算子，因為轉換運算子無法採用額外參數。  它也不適用於 [variadic](../cpp/ellipses-and-variadic-templates.md) 建構函式，因為加入額外參數會讓函式參數封裝非推算內容，進而讓 `enable_if` 的目的失敗。  
  
 情節 3 使用名稱 `Dummy`，但它是選擇性的。 只用 "`typename = typename`" 也可以，但如果您認為這樣看起來不妥，則可以使用 "dummy" 名稱；只要不要用到函式定義中可能也會使用的名稱即可。 如果您未指定 `enable_if` 的類型，則會預設為 void，而且這十分合理，因為您不在意 `Dummy` 是什麼。 這適用於所有項目 (包括轉換運算子和 [variadic](../cpp/ellipses-and-variadic-templates.md) 建構函式)。  
  
 情節 4 適用於沒有傳回型別的建構函式，進而解決情節 1 的包裝限制。  不過，情節 4 是限制為非範本函式引數，但這些引數不一定可用  (在範本函式引數上使用情節 4，可防止範本引數推算處理它)。  
  
 `enable_if` 功能十分強大，但是誤用也十分危險。  因為它的目的是讓候選項在多載解析之前消失，所以誤用的效果可能會讓人十分混淆。  部分建議如下：  
  
-   請勿使用 `enable_if`，在編譯時期選取不同的實作。 請勿針對 `enable_if` 寫入一個 `CONDITION`，而針對 `!CONDITION` 寫入另一個。  請改用「標記分派」模式，例如，根據提供給實作的迭代器強度來選取實作的演算法。  
  
-   請勿使用 `enable_if` 來強制執行需求。  如果您想要驗證範本參數，但驗證失敗而導致錯誤，則請改用 [static_assert](../cpp/static-assert.md)，而不要選取另一個實作。  
  
-   當您的多載集讓良好的程式碼變得模稜兩可時，請使用 `enable_if`。  這最常發生在隱含轉換建構函式中。  
  
## <a name="example"></a>範例  
 此範例說明 C++ 標準程式庫範本函式 [std::make_pair()](../standard-library/utility-functions.md#make_pair) 如何利用 `enable_if`。  
  
```cpp  
void func(const pair<int, int>&);

void func(const pair<string, string>&);

func(make_pair("foo", "bar"));
```  
  
  在此範例中，`make_pair("foo", "bar")` 會傳回 `pair<const char *, const char *>`。 多載解析必須判斷您要的 `func()`。 `pair<A, B>` 具有來自 `pair<X, Y>` 的隱含轉換建構函式。  這不是新功能，而是 C++98 中的功能。 不過，在 C++98/03 中，一律會有隱含轉換建構函式的簽章，即使是 `pair<int, int>(const pair<const char *, const char *>&)` 也是一樣。  多載解析不在意具現化該建構函式的嘗試急遽增加，因為 `const char *` 不會隱含地轉換為 `int`；在函式定義具現化之前，它只會查看簽章。  因此，此範例程式碼會模稜兩可，因為有簽章可以將 `pair<const char *, const char *>` 轉換為 `pair<int, int>` 和 `pair<string, string>`。  
  
 C++11 已解決這項模稜兩可，方法是使用 `enable_if` 來確定**僅有當 ** `const X&` 可隱含轉換為 `A` 且 `const Y&` 可隱含轉換為 `B` 時，`pair<A, B>(const pair<X, Y>&)` 才存在。  這讓多載解析可以判斷 `pair<const char *, const char *>` 不可轉換為 `pair<int, int>`，而且採用 `pair<string, string>` 的多載是可行的。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)




