---
title: SafeInt 類別
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeInt
- SafeInt::SafeInt
- SafeInt.SafeInt
helpviewer_keywords:
- SafeInt class
- SafeInt class, constructor
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
ms.openlocfilehash: 97d81401cfd01d6d39457a9d63c39bc25901128e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219348"
---
# <a name="safeint-class"></a>SafeInt 類別

擴充基本整數型別，有助於防止整數溢位，並讓您比較不同的整數型別。

> [!NOTE]
> 最新版的 SafeInt 程式庫位於 [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt) 。 若要使用 SafeInt 程式庫，請複製儲存機制和`#include "SafeInt.hpp"`

## <a name="syntax"></a>語法

```cpp
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>
class SafeInt;
```

### <a name="parameters"></a>參數

| [範本]  |  說明 |
|--------|------------|
| T         |  `SafeInt` 所取代的整數或布林值參數型別。 |
| E         |  定義錯誤處理原則的列舉資料型別。 |
| U         |  適用於第二個運算元的整數或布林值參數型別。 |

| 參數  |  說明 |
|---------|-----------------|
| *rhs*      |  [in] 輸入的參數，在數個獨立函式中代表運算子右邊的值。 |
| *i*        |  [in] 輸入的參數，在數個獨立函式中代表運算子右邊的值。 |
| *一些*     |  [in] 輸入的參數，在數個獨立函式中代表運算子右邊的值。 |

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

| 名稱                          |  說明 |
|---------------------------|--------------------|
| [SafeInt::SafeInt](#safeint)  |  預設建構函式。 |

### <a name="assignment-operators"></a>指派運算子

| Name  |  語法 |
|----|---------|
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const U& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const T& rhs) throw()` |
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()` |

### <a name="casting-operators"></a>轉型運算子

| Name              |  語法 |
|------|---------------------------------|
| bool              |  `operator bool() throw()` |
| char              |  `operator char() const` |
| signed char       |  `operator signed char() const` |
| unsigned char     |  `operator unsigned char() const` |
| __int16           |  `operator __int16() const` |
| unsigned __int16  |  `operator unsigned __int16() const` |
| __int32           |  `operator __int32() const` |
| unsigned __int32  |  `operator unsigned __int32() const` |
| long              |  `operator long() const` |
| unsigned long     |  `operator unsigned long() const` |
| __int64           |  `operator __int64() const` |
| unsigned __int64  |  `operator unsigned __int64() const` |
| wchar_t           |  `operator wchar_t() const` |

### <a name="comparison-operators"></a>比較運算子

| Name  |  語法 |
|----|----------------|
| \<     |  `template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()` |
| \<     |  `bool operator< (SafeInt<T,E> rhs) const throw()` |
| \>=    |  `template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()` |
| \>=    |  `Bool operator>= (SafeInt<T,E> rhs) const throw()` |
| \>     |  `template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()` |
| \>     |  `Bool operator> (SafeInt<T,E> rhs) const throw()` |
| \<=    |  `template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()` |
| \<=    |  `bool operator<= (SafeInt<T,E> rhs) const throw()` |
| ==    |  `template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()` |
| ==    |  `bool operator== (bool rhs) const throw()` |
| ==    |  `bool operator== (SafeInt<T,E> rhs) const throw()` |
| !=    |  `template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()` |
| !=    |  `bool operator!= (bool b) const throw()` |
| !=    |  `bool operator!= (SafeInt<T,E> rhs) const throw()` |

### <a name="arithmetic-operators"></a>算術運算子

| Name  |  語法 |
|----|--------------|
| +     |  `const SafeInt<T,E>& operator+ () const throw()` |
| -     |  `SafeInt<T,E> operator- () const` |
| ++    |  `SafeInt<T,E>& operator++ ()` |
| --    |  `SafeInt<T,E>& operator-- ()` |
| %     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const` |
| %     |  `SafeInt<T,E> operator% (SafeInt<T,E> rhs) const` |
| %=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)` |
| %=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)` |
| \*     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const` |
| \*     |  `SafeInt<T,E> operator* (SafeInt<T,E> rhs) const` |
| \*=    |  `SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)` |
| \*=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)` |
| \*=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)` |
| /     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const` |
| /     |  `SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const` |
| /=    |  `SafeInt<T,E>& operator/= (SafeInt<T,E> i)` |
| /=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)` |
| /=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)` |
| +     |  `SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const` |
| +     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const` |
| +=    |  `SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)` |
| +=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)` |
| +=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)` |
| -     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const` |
| -     |  `SafeInt<T,E> operator- (SafeInt<T,E> rhs) const` |
| -=    |  `SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)` |
| -=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)` |
| -=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)` |

### <a name="logical-operators"></a>邏輯運算子

| Name     |  語法 |
|------|--------------|
| !        |  `bool operator !() const throw()` |
| ~        |  `SafeInt<T,E> operator~ () const throw()` |
| \<\<       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()` |
| \<\<       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()` |
| \<\<=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()` |
| \<\<=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()` |
| \>\>       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()` |
| \>\>       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()` |
| \>\>=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()` |
| \>\>=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()` |
| &        |  `SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()` |
| &        |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()` |
| &=       |  `SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()` |
| &=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()` |
| &=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()` |
| ^        |  `SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()` |
| ^        |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()` |
| ^=       |  `SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()` |
| ^=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()` |
| ^=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()` |
| &#124;   |  `SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()` |
| &#124;   |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()` |
| &#124;=  |  `SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()` |
| &#124;=  |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()` |
| &#124;=  |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()` |

## <a name="remarks"></a>備註

`SafeInt` 類別可在算術運算中防止整數溢位。 例如，考慮加入兩個 8 位元整數：一個值為 200 的整數，第二個則是值為 100 的整數。 正確的數學運算為 200 + 100 = 300。 不過，由於 8 位元整數的限制，因此將遺失高位元，而編譯器將傳回 44 (300 - 2<sup>8</sup>) 做為結果。 取決於此數學方程式的任何作業都將產生非預期的行為。

`SafeInt` 類別會檢查是否發生算術溢位，或者程式碼是否嘗試除以零。 在這兩種情況下，此類別都會呼叫錯誤處理常式來警告程式可能會發生此問題。

此類別也可讓您比較兩個不同型別的整數，但前提是它們均為 `SafeInt` 物件。 一般而言，當您進行比較時，必須先將數位轉換成相同的類型。 將一個數字轉換為其他型別，通常需要進行檢查，以確定並未遺失資料。

本主題中的運算子表格會列出 `SafeInt` 類別所支援的數學和比較運算子。 大多數的數學運算子都會傳回型別 `T` 的 `SafeInt` 物件。

`SafeInt` 和整數型別間的比較作業可以任一方向執行。 例如，`SafeInt<int>(x) < y` 和 `y> SafeInt<int>(x)` 均有效且將傳回相同結果。

許多二元運算子都不支援使用兩種不同 `SafeInt` 的類型。 這其中一個範例是 `&` 運算子。 `SafeInt<T, E> & int`是支援的，但 `SafeInt<T, E> & SafeInt<U, E>` 不是。 在第二個範例中，編譯器不知道要傳回的參數型別。 此問題的解決方案之一是將第二個參數轉換回基底型別。 使用相同的參數，就能透過 `SafeInt<T, E> & (U)SafeInt<U, E>` 來完成此動作。

> [!NOTE]
> 針對任何位元運算，這兩個不同的參數應為相同大小。 如果大小不同，編譯器將擲回 [ASSERT](../mfc/reference/diagnostic-services.md#assert) 例外狀況。 這項作業的結果無法保證正確。 若要解決此問題，請轉換較小的參數，直到它的大小與較大的參數相同。

針對移位運算子，若移位的位元數較範本型別現有的位元數還多，則將擲回 ASSERT 例外狀況。 這在發行模式中將不會產生任何作用。 移位運算子可能會混用兩種型別的 SafeInt 參數，因為傳回型別與原始型別相同。 運算子右邊的數字只代表要移位的位元數。

當您使用 SafeInt 物件進行邏輯比較時，比較就是嚴格的算數運算。 例如，考慮下列運算式：

- `SafeInt<uint>((uint)~0) > -1`

- `((uint)~0) > -1`

第一個語句會解析為 **`true`** ，但第二個語句會解析為 **`false`** 。 0 的位元否定為 0xFFFFFFFF。 在第二個陳述式中，預設的比較運算子會比較 0xFFFFFFFF 和 0xFFFFFFFF，並將它們視為相等。 `SafeInt` 類別的比較運算子發現第二個參數為負數，而第一個參數不帶正負號。 因此，儘管位元表示法完全相同，但 `SafeInt` 邏輯運算子發現不帶正負號的整數大於 -1。

當您將 `SafeInt` 類別搭配 `?:` 三元運算子一起使用時要小心。 請考慮下列程式碼行。

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : -1;
```

編譯器會將它轉換為如下內容：

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);
```

如果 `flag` 為 **`false`** ，編譯器會擲回例外狀況，而不是將-1 的值指派給 `x` 。 因此，為了避免此行為，請使用下列這一行正確的程式碼。

```cpp
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;
```

您可以為 `T` 和 `U` 指派布林值型別、字元型別或整數型別。 整數型別不一定要帶正負號，且大小從 8 位元到 64 位元均可。

> [!NOTE]
> 雖然 `SafeInt` 類別接受任何種類的整數，但它搭配不帶正負號的型別執行會更有效率。

`E` 是 `SafeInt` 所使用的錯誤處理機制。 SafeInt 程式庫提供了兩種錯誤處理機制。 預設原則為 `SafeIntErrorPolicy_SafeIntException`，其會在發生錯誤時擲回 [SafeIntException 類別](safeintexception-class.md)例外狀況。 另一個原則是 `SafeIntErrorPolicy_InvalidParameter`，其會在發生錯誤時停止程式。

自訂錯誤原則的方法有兩種。 第一個選項是當您建立 `SafeInt` 時設定參數 `E`。 當您只想針對一個 `SafeInt` 變更錯誤處理原則時，請使用此選項。 另一個選項是先定義 _SAFEINT_DEFAULT_ERROR_POLICY 作為您自訂的錯誤處理類別，然後再納入 `SafeInt` 程式庫。 當您想要針對程式碼中 `SafeInt` 類別的所有執行個體變更預設的錯誤處理原則時，請選擇此選項。

> [!NOTE]
> 處理來自 SafeInt 程式庫之錯誤的自訂類別，不應將控制權傳回給呼叫錯誤處理常式的程式碼。 呼叫錯誤處理常式之後，就無法信任作業的結果 `SafeInt` 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`SafeInt`

## <a name="requirements"></a>需求

**標頭：** SafeInt. 措施
> [!NOTE]
> 此程式庫的最新版本位於 [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt) 。 複製程式庫，並包含 SafeInt. 措施以使用 SafeInt 程式庫。
> 偏好此 github 存放庫以 <safeint>。 這是 <safeint 的新式>，其中包含少數 bug 修正、使用 c + + 的現代化功能，因而產生更有效率的程式碼，並可移植到任何使用 gcc、clang 或 Intel 編譯器的平臺。

### <a name="example"></a>範例

```c
#include "SafeInt.hpp" // set path to your clone of the SafeInt GitHub repo (https://github.com/dcleblanc/SafeInt)

int main()
{
    int divisor = 3;
    int dividend = 6;
    int result;

    bool success = SafeDivide(dividend, divisor, result); // result = 2
    success = SafeDivide(dividend, 0, result); // expect fail. result isn't modified.
}
```

**命名空間：** 無

## <a name="safeintsafeint"></a><a name="safeint"></a>SafeInt：： SafeInt

建構 `SafeInt` 物件。

```cpp
SafeInt() throw

SafeInt (const T& i) throw ()

SafeInt (bool b) throw ()

template <typename U>
SafeInt (const SafeInt <U, E>& u)

I template <typename U>
SafeInt (const U& i)
```

### <a name="parameters"></a>參數

`i`<br/>
[in] 新 `SafeInt` 物件的值。 根據建構函式而定，這必須是型別 T 或 U 的參數。

`b`<br/>
[in] 新 `SafeInt` 物件的布林值。

`u`<br/>
[in] 型別 U 的 `SafeInt`。新 `SafeInt` 物件的值將會與 *u* 相同，但型別將為 T。

`U`儲存在中的資料類型 `SafeInt` 。 這可以是布林值、字元或整數型別。 如果是整數類型，則可以是帶正負號或不帶正負號的，並介於8到64位之間。

### <a name="remarks"></a>備註

建構函式的輸入參數 *i* 或 *u* 必須是布林值、字元或整數型別。 如果它是另一種參數類型， `SafeInt` 類別會呼叫[static_assert](../cpp/static-assert.md)來指出不正確輸入參數。

使用範本型別 `U` 的建構函式會將輸入參數自動轉換為 `T` 所指定的型別。 `SafeInt` 類別會轉換資料且不會遺失任何資料。 `E`如果無法將資料轉換成類型 `T` 而不會遺失資料，它會向錯誤處理常式報告。

如果您從布林值參數建立 `SafeInt`，則必須立即將值初始化。 您無法使用程式 `SafeInt` 代碼來建立 `SafeInt<bool> sb;` 。 這將產生編譯錯誤。
