---
title: "SafeInt 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "SafeInt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeInt 類別"
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
caps.latest.revision: 16
caps.handback.revision: 16
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# SafeInt 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

擴充整數原始有助於防止整數溢位而讓您比較整數的 Variant 型別。  
  
## 語法  
  
```  
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>  
class SafeInt;  
```  
  
#### 參數  
  
|範本|說明|  
|--------|--------|  
|T|`SafeInt` 取代整數或布林值參數的型別。|  
|E|定義錯誤處理原則的列舉資料型別。|  
|U|整數或布林值參數型別的第二個運算元。|  
  
|參數|說明|  
|--------|--------|  
|\[in\] rhs|在多個函式的運算子右方的表示值的輸入參數。|  
|\[in\] i|在多個函式的運算子右方的表示值的輸入參數。|  
|\[in\] 位元|在多個函式的運算子右方的表示值的輸入參數。|  
  
## 成員  
  
### 公用建構函式  
  
|Name|說明|  
|----------|--------|  
|[SafeInt::SafeInt](../windows/safeint-safeint.md)|預設建構函式。|  
  
### 指派運算子  
  
|Name|語法|  
|----------|--------|  
|\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const U& rhs)`|  
|\=|`SafeInt<T,E>& operator= (const T& rhs) throw()`|  
|\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)`|  
|\=|`SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()`|  
  
### 轉型運算子  
  
|Name|語法|  
|----------|--------|  
|bool|`operator bool() throw()`|  
|char|`operator char() const`|  
|signed char|`operator signed char() const`|  
|unsigned char|`operator unsigned char() const`|  
|\_\_int16|`operator __int16() const`|  
|unsigned \_\_int16|`operator unsigned __int16() const`|  
|\_\_int32|`operator __int32() const`|  
|unsigned \_\_int32|`operator unsigned __int32() const`|  
|long|`operator long() const`|  
|unsigned long|`operator unsigned long() const`|  
|\_\_int64|`operator __int64() const`|  
|unsigned \_\_int64|`operator unsigned __int64() const`|  
|wchar\_t|`operator wchar_t() const`|  
  
### 比較運算子  
  
|Name|語法|  
|----------|--------|  
|\<|`template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()`|  
|\<|`bool operator< (SafeInt<T,E> rhs) const throw()`|  
|\>\=|`template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()`|  
|\>\=|`Bool operator>= (SafeInt<T,E> rhs) const throw()`|  
|\>|`template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()`|  
|\>|`Bool operator> (SafeInt<T,E> rhs) const throw()`|  
|\<\=|`template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()`|  
|\<\=|`bool operator<= (SafeInt<T,E> rhs) const throw()`|  
|\=\=|`template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()`|  
|\=\=|`bool operator== (bool rhs) const throw()`|  
|\=\=|`bool operator== (SafeInt<T,E> rhs) const throw()`|  
|\!\=|`template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()`|  
|\!\=|`bool operator!= (bool b) const throw()`|  
|\!\=|`bool operator!= (SafeInt<T,E> rhs) const throw()`|  
  
### 算術運算子  
  
|Name|語法|  
|----------|--------|  
|\+|`const SafeInt<T,E>& operator+ () const throw()`|  
|\-|`SafeInt<T,E> operator- () const`|  
|\+\+|`SafeInt<T,E>& operator++ ()`|  
|\-\-|`SafeInt<T,E>& operator-- ()`|  
|%|`template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const`|  
|%|`SafeInt<T,E> operator% (SafeInt<T,E> rhs) const`|  
|%\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)`|  
|%\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)`|  
|\*|`template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const`|  
|\*|`SafeInt<T,E> operator* (SafeInt<T,E> rhs) const`|  
|\*\=|`SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)`|  
|\*\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)`|  
|\*\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)`|  
|\/|`template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const`|  
|\/|`SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const`|  
|\/\=|`SafeInt<T,E>& operator/= (SafeInt<T,E> i)`|  
|\/\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)`|  
|\/\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)`|  
|\+|`SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const`|  
|\+|`template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const`|  
|\+\=|`SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)`|  
|\+\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)`|  
|\+\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)`|  
|\-|`template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const`|  
|\-|`SafeInt<T,E> operator- (SafeInt<T,E> rhs) const`|  
|\-\=|`SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)`|  
|\-\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)`|  
|\-\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)`|  
  
### 邏輯運算子  
  
|Name|語法|  
|----------|--------|  
|\!|`bool operator !() const throw()`|  
|~|`SafeInt<T,E> operator~ () const throw()`|  
|\<\<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()`|  
|\<\<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()`|  
|\<\<\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()`|  
|\<\<\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()`|  
|\>\>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()`|  
|\>\>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()`|  
|\>\>\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()`|  
|\>\>\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()`|  
|&|`SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()`|  
|&|`template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()`|  
|&\=|`SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()`|  
|&\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()`|  
|&\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()`|  
|^|`SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()`|  
|^|`template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()`|  
|^\=|`SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()`|  
|^\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()`|  
|^\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()`|  
|&#124;|`SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()`|  
|&#124;|`template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()`|  
|&#124;\=|`SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()`|  
|&#124;\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()`|  
|&#124;\=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()`|  
  
## 備註  
 `SafeInt` 類別可防止在算術運算的整數溢位。  例如，請考慮將兩個 8 位元整數:具有值為 200，而第二個具有 100 的值。  正確的算術運算是 200 \+ 100 \= 300。  然而，因為 8 位元整數限制，較高位元會遺失，而且編譯器會傳回 44 \(300 \- 2<sup>8</sup>\)做為結果。  取決於這個數學方程式的作業將會產生非預期的行為。  
  
 `SafeInt` 類別會檢查的算術溢位是否產生或程式碼是否嘗試除以零。  在這兩種情況下，類別會呼叫錯誤處理常式警告此潛在問題的程式。  
  
 只要是 `SafeInt` 物件，這個類別也可讓您比較整數的兩個不同型別。  通常，當您執行比較時，您必須先將數字轉換為相同型別。  轉換為另一個型別的數字通常需要檢查，以確定沒有資料遺失。  
  
 本主題中的運算子表列出數學，而且 `SafeInt` 支援的比較運算子分類。  大多數算術運算子傳回型別 `T`的 `SafeInt` 物件。  
  
 在 `SafeInt` 和整數類資料型別之間的比較作業可以在任一方向進行。  例如， `SafeInt<int>(x) < y` 和 `y > SafeInt<int>(x)` 有效，並傳回相同的結果。  
  
 使用兩個不同的 `SafeInt` 型別，許多二元運算子不支援。  這個範例是 `&` 運算子。  支援`SafeInt<T, E> & int` ，不過 `SafeInt<T, E> & SafeInt<U, E>` 不支援。  在這個第二個範例中，編譯器不知道傳回的參數。  對這個問題的解決方案是轉換為第二參數回到基底型別。  使用相同的參數，這可以與 `SafeInt<T, E> & (U)SafeInt<U, E>`。  
  
> [!NOTE]
>  對於所有位元運算，如果兩個不同參數應該是相同大小。  如果大小不同，編譯器將會擲回 [ASSERT](../Topic/ASSERT%20\(MFC\).md) 例外狀況。  這個運算的結果無法保證是正確的。  若要解決這個問題，請轉換較小的參數，直到它是相同大小較大的參數。  
  
 對於移位運算子，將更多的範本類型存在會擲回判斷提示例外狀況。  這在發行模式中不會有任何作用。  因為傳回型別是與原始型別，混合 SafeInt 參數的兩種類型的移位運算子是可能的。  在運算子右方的數字只表示位元數對傳輸。  
  
 當您執行邏輯比較與 SafeInt 物件時，比較完全是運算。  例如，請考慮下列運算式:  
  
-   `SafeInt<uint>((uint)~0) > -1`  
  
-   `((uint)~0) > -1`  
  
 第一個陳述式會解析為 `true`，不過第二個陳述式會解析為 `false`。  位元負 0 為 0xFFFFFFFF。  在第二個陳述式，預設比較運算子與 0xFFFFFFFF 比較 0xFFFFFFFF 並會將它們視為相等。  `SafeInt` 類別的比較運算子注意第二個參數是負的，而第一個參數是 unsigned。  因此，不過位元表示相同， `SafeInt` 邏輯運算子發現不帶正負號的整數大於 \-1。  
  
 當您使用 `?:` 三元運算子時，使用 `SafeInt` 類別小心。  假設有以下程式碼。  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : -1;  
```  
  
 編譯器無法在此兩者之間進行轉換:  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);  
```  
  
 如果 `flag` 是 `false`，編譯器會擲回例外狀況而不是將值 \-1 傳遞至此 `x`。  因此，避免這種行為，正確的程式碼是使用下列程式碼行。  
  
```  
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;  
```  
  
 `T` 和 `U` 可以指派布林型別、字元型別或整數型別。  整數型別可以是帶正負號或不帶正負號和從 8 位元的任何大小為 64 位元。  
  
> [!NOTE]
>  雖然 `SafeInt` 類別接受任何種類的整數，更有效率地執行與不帶正負號的型別。  
  
 `E` 為 `SafeInt` 時要使用的錯誤處理機制。  兩個錯誤處理機制提供 SafeInt 程式庫。  預設原則是， 當錯誤發生時，`SafeIntErrorPolicy_SafeIntException`會擲回 [SafeIntException 類別](../windows/safeintexception-class.md) 例外狀況，。  另一個原則是 `SafeIntErrorPolicy_InvalidParameter`，如果發生錯誤則停止程式。  
  
 有兩個選擇自訂錯誤原則。  在建立 `SafeInt`時，第一個選項是將參數設定為 `E` 。  例如，當您想要變更為 `SafeInt`時，錯誤處理原則才使用此選項。  包含在 `SafeInt` 程式庫之前，另一種方式是定義 `_SAFEINT_DEFAULT_ERROR_POLICY` 是自訂的錯誤處理類別。  例如，當您想要變更 `SafeInt` 類別所有執行個體的預設錯誤處理原則程式碼時，請使用這個選項。  
  
> [!NOTE]
>  處理來自 SafeInt 程式庫的錯誤的自訂類別不應該將控制項傳回到呼叫錯誤處理常式的程式碼。  在錯誤處理常式呼叫後， `SafeInt` 作業的結果無法信任。  
  
## 需求  
 **標頭：** safeint.h  
  
 **命名空間：** msl::utilities  
  
## 請參閱  
 [Miscellaneous Support Libraries Classes](http://msdn.microsoft.com/zh-tw/406fd46e-d53f-4096-ab40-36aa754c7a5c)   
 [SafeInt 程式庫](../windows/safeint-library.md)   
 [SafeIntException 類別](../windows/safeintexception-class.md)