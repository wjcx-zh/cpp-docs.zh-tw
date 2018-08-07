---
title: SafeInt 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeInt
dev_langs:
- C++
helpviewer_keywords:
- SafeInt class
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c1e4ac8898b48c4b64d0b12b945ab45b1c5f1436
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606152"
---
# <a name="safeint-class"></a>SafeInt 類別
擴充整數基本項目，來協助防止整數溢位，並可讓您比較不同類型的整數。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>  
class SafeInt;  
```  
  
### <a name="parameters"></a>參數  
  
|範本|描述|  
|--------------|-----------------|  
|T|整數或布林值參數的型別， **SafeInt**取代。|  
|E|列舉的資料型別定義的錯誤處理原則。|  
|U|整數或布林值的參數，第二個運算元的型別。|  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*rhs*|輸入的參數，表示數個獨立的函式中的運算子右邊的值。|  
|[in]*我*|輸入的參數，表示數個獨立的函式中的運算子右邊的值。|  
|[in]*位元*|輸入的參數，表示數個獨立的函式中的運算子右邊的值。|  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[SafeInt::SafeInt](../windows/safeint-safeint.md)|預設建構函式。|  
  
### <a name="assignment-operators"></a>指派運算子  
  
|名稱|語法|  
|----------|------------|  
|=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const U& rhs)`|  
|=|`SafeInt<T,E>& operator= (const T& rhs) throw()`|  
|=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)`|  
|=|`SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()`|  
  
### <a name="casting-operators"></a>轉型運算子  
  
|名稱|語法|  
|----------|------------|  
|bool|`operator bool() throw()`|  
|char|`operator char() const`|  
|signed char|`operator signed char() const`|  
|unsigned char|`operator unsigned char() const`|  
|__int16|`operator __int16() const`|  
|unsigned __int16|`operator unsigned __int16() const`|  
|__int32|`operator __int32() const`|  
|unsigned __int32|`operator unsigned __int32() const`|  
|long|`operator long() const`|  
|unsigned long|`operator unsigned long() const`|  
|__int64|`operator __int64() const`|  
|unsigned __int64|`operator unsigned __int64() const`|  
|wchar_t|`operator wchar_t() const`|  
  
### <a name="comparison-operators"></a>比較運算子  
  
|名稱|語法|  
|----------|------------|  
|<|`template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()`|  
|<|`bool operator< (SafeInt<T,E> rhs) const throw()`|  
|>=|`template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()`|  
|>=|`Bool operator>= (SafeInt<T,E> rhs) const throw()`|  
|>|`template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()`|  
|>|`Bool operator> (SafeInt<T,E> rhs) const throw()`|  
|<=|`template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()`|  
|<=|`bool operator<= (SafeInt<T,E> rhs) const throw()`|  
|==|`template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()`|  
|==|`bool operator== (bool rhs) const throw()`|  
|==|`bool operator== (SafeInt<T,E> rhs) const throw()`|  
|!=|`template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()`|  
|!=|`bool operator!= (bool b) const throw()`|  
|!=|`bool operator!= (SafeInt<T,E> rhs) const throw()`|  
  
### <a name="arithmetic-operators"></a>算術運算子  
  
|名稱|語法|  
|----------|------------|  
|+|`const SafeInt<T,E>& operator+ () const throw()`|  
|-|`SafeInt<T,E> operator- () const`|  
|++|`SafeInt<T,E>& operator++ ()`|  
|--|`SafeInt<T,E>& operator-- ()`|  
|%|`template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const`|  
|%|`SafeInt<T,E> operator% (SafeInt<T,E> rhs) const`|  
|%=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)`|  
|%=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)`|  
|*|`template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const`|  
|*|`SafeInt<T,E> operator* (SafeInt<T,E> rhs) const`|  
|*=|`SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)`|  
|*=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)`|  
|*=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)`|  
|/|`template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const`|  
|/|`SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const`|  
|/=|`SafeInt<T,E>& operator/= (SafeInt<T,E> i)`|  
|/=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)`|  
|/=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)`|  
|+|`SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const`|  
|+|`template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const`|  
|+=|`SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)`|  
|+=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)`|  
|+=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)`|  
|-|`template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const`|  
|-|`SafeInt<T,E> operator- (SafeInt<T,E> rhs) const`|  
|-=|`SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)`|  
|-=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)`|  
|-=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)`|  
  
### <a name="logical-operators"></a>邏輯運算子  
  
|名稱|語法|  
|----------|------------|  
|!|`bool operator !() const throw()`|  
|~|`SafeInt<T,E> operator~ () const throw()`|  
|<<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()`|  
|<<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()`|  
|<<=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()`|  
|<<=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()`|  
|>>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()`|  
|>>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()`|  
|>>=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()`|  
|>>=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()`|  
|&|`SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()`|  
|&|`template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()`|  
|&=|`SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()`|  
|&=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()`|  
|&=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()`|  
|^|`SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()`|  
|^|`template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()`|  
|^=|`SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()`|  
|^=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()`|  
|^=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()`|  
|&#124;|`SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()`|  
|&#124;|`template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()`|  
|&#124;=|`SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()`|  
|&#124;=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()`|  
|&#124;=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()`|  
  
## <a name="remarks"></a>備註  
 **SafeInt**類別可防止整數溢位在數學運算。 例如，請考慮新增兩個 8 位元整數： 其中一個其值為 200，而且第二個為 100 的值。 正確的數學運算會是 200 + 100 = 300。 不過，8 位元整數的限制，因為上方的位元會遺失，而且編譯器會傳回 44 (300 2<sup>8</sup>) 做為結果。 取決於這個數學方程式的任何作業將會產生非預期的行為。  
  
 **SafeInt**類別會檢查是否發生算術溢位或程式碼是否會嘗試除以零。 在這兩種情況下，類別會呼叫錯誤處理常式的潛在問題的程式，即發出警告。  
  
 這個類別也可讓您比較兩種不同的整數，只要它們**SafeInt**物件。 一般而言，當您執行比較時，您必須先轉換為相同類型的數字。 轉型成其他類型的一個數字時，通常需要檢查，以確定沒有不遺失資料。  
  
 本主題中的運算子資料表會列出所支援的數學和比較運算子**SafeInt**類別。 最數學運算子會傳回**SafeInt**型別的物件`T`。  
  
 之間的比較作業**SafeInt**和整數型別可以在任一方向中執行。 例如，同時`SafeInt<int>(x) < y`和`y> SafeInt<int>(x)`有效，並且會傳回相同的結果。  
  
 許多二元運算子不支援使用兩個不同**SafeInt**型別。 這其中一個範例是`&`運算子。 `SafeInt<T, E> & int` 支援，但`SafeInt<T, E> & SafeInt<U, E>`不是。 在第二個範例中，編譯器不知道要傳回參數的類型。 此問題的解決方案之一是要轉換成基底型別第二個參數。 使用相同的參數，做法是使用`SafeInt<T, E> & (U)SafeInt<U, E>`。  
  
> [!NOTE]
>  對於任何位元運算，兩個不同的參數應為相同的大小。 如果大小不同，編譯器將會擲回[ASSERT](../mfc/reference/diagnostic-services.md#assert)例外狀況。 若要取得精確，無法保證這項作業的結果。 若要解決此問題，將參數轉型較小的較大的參數相同的大小為止。  
  
 移位運算子，移位的位元非範本類型存在的更多將會擲回判斷提示例外狀況。 這會在發行模式中有任何作用。 移位運算子可能混用兩種類型的 SafeInt 參數會因為傳回的類型是原始的型別相同。 運算子的右邊數只表示移位位元數的字。  
  
 當您執行與一個 SafeInt 物件的邏輯比較時，比較不嚴格算術。 例如，請考慮這些運算式：  
  
-   `SafeInt<uint>((uint)~0) > -1`  
  
-   `((uint)~0) > -1`  
  
 第一個陳述式會解析成**真**，但第二個陳述式會解析成**false**。 0 位元否定是 0xFFFFFFFF。 在第二個陳述式中，預設的比較運算子比較 0xFFFFFFFF 以 0xFFFFFFFF，並且會考慮它們會相等。 比較運算子**SafeInt**類別體認到第二個參數是負的而第一個參數是不帶正負號。 因此，位元表示完全相同，不過**SafeInt**邏輯運算子可讓您發現的不帶正負號的整數大於-1。  
  
 當您使用時要小心**SafeInt**類別搭配`?:`三元運算子。 請考慮下列程式碼行。  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : -1;  
```  
  
 編譯器會將它轉換成這樣：  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);  
```  
  
 如果`flag`已**假**，編譯器就會擲回的例外狀況，而不是-1 的值，指派`x`。 因此，若要避免此行為，若要使用正確的程式碼是下面這一行。  
  
```  
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;  
```  
  
 `T` 和`U`布林型別、 字元類型或整數類型可以指派。 類型可以帶正負號或不帶正負號的整數，從 8 位元到 64 位元的任何大小。  
  
> [!NOTE]
>  雖然**SafeInt**類別接受任何類型的整數，它會執行更有效率地與不帶正負號的類型。  
  
 `E` 是的錯誤處理機制可**SafeInt**使用。 SafeInt 程式庫會提供兩種錯誤處理機制。 預設原則`SafeIntErrorPolicy_SafeIntException`，哪些則會擲回[SafeIntException 類別](../windows/safeintexception-class.md)發生錯誤時的例外狀況。 另一項原則是`SafeIntErrorPolicy_InvalidParameter`，這樣會停止程式，如果發生錯誤。  
  
 有兩個選項來自訂錯誤原則。 第一個選項是設定參數`E`當您建立**SafeInt**。 使用此選項，當您想要變更的錯誤處理原則的其中一個**SafeInt**。 另一個選項是定義為您自訂的錯誤處理類別後再納入 _SAFEINT_DEFAULT_ERROR_POLICY **SafeInt**程式庫。 使用此選項，當您想要變更預設的錯誤處理原則的所有執行個體**SafeInt**程式碼中的類別。  
  
> [!NOTE]
>  處理來自 SafeInt 程式庫錯誤的自訂的類別不應傳回控制項以呼叫錯誤處理常式的程式碼。 錯誤處理常式呼叫時，結果之後**SafeInt**作業無法受到信任。  
  
## <a name="requirements"></a>需求  
 **標頭：** safeint.h  
  
 **命名空間：** msl:: utilities  
  
## <a name="see-also"></a>另請參閱  
 [SafeInt 程式庫](../windows/safeint-library.md)   
 [SafeIntException 類別](../windows/safeintexception-class.md)