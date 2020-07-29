---
title: 運算子多載
ms.date: 11/04/2016
f1_keywords:
- operator_cpp
- operator
helpviewer_keywords:
- redefinable operators [C++]
- non-redefinable operators [C++]
- operator keyword [C++]
- operators [C++], overloading
- operator overloading
ms.assetid: 56ad4c4f-dd0c-45e0-adaa-08fe98cb1f8e
ms.openlocfilehash: 822bd5efb3125e69ff60aa42ba6419969cace403
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227227"
---
# <a name="operator-overloading"></a>運算子多載

關鍵字會宣告 **`operator`** *函式*，以指定套用至類別實例時的運算子符號。 這讓運算子有多個意義，或稱為「多載」。 編譯器會檢查運算元的類型，以區別運算子的不同意義。

## <a name="syntax"></a>語法

> *類型* **`operator`***operator-符號* **（** *參數清單* **）**

## <a name="remarks"></a>備註

您可以用全域方式或以逐一類別為基礎，重新定義大多數內建運算子的函式。 多載運算子實做為函式。

多載運算子的名稱是 **`operator`** *x*，其中*x*是下表中顯示的運算子。 例如，若要多載加號，請定義稱為**operator + 的函**式。 同樣地，若要多載加法/指派運算子， **+=** 請定義稱為**operator + = 的函**式。

### <a name="redefinable-operators"></a>可重新定義的運算子

|運算子|名稱|類型|
|--------------|----------|----------|
|**,**|Comma (逗號)|Binary|
|**!**|邏輯 NOT|一元 (Unary)|
|**!=**|不等|Binary|
|**%**|模組|Binary|
|**%=**|模數指派|Binary|
|**&**|位元 AND|Binary|
|**&**|傳址|一元 (Unary)|
|**&&**|邏輯 AND|Binary|
|**&=**|位元 AND 指派|Binary|
|**( )**|函式呼叫|—|
|**( )**|轉換運算子|一元 (Unary)|
|**&#42;**|乘|Binary|
|**&#42;**|指標取值 (Dereference)|一元 (Unary)|
|**&#42;=**|乘法指派|Binary|
|**+**|加法|Binary|
|**+**|一元加號|一元 (Unary)|
|**++**|增量<sup>1</sup>|一元 (Unary)|
|**+=**|加法指派|Binary|
|**-**|減|Binary|
|**-**|一元負運算|一元 (Unary)|
|**--**|遞減<sup>1</sup>|一元 (Unary)|
|**-=**|減法指派|Binary|
|**->**|成員選取|Binary|
|**->&#42;**|成員指標選取|Binary|
|**/**|部門|Binary|
|**/=**|除法指派|Binary|
|**\<**|小於|Binary|
|**<<**|左移|Binary|
|**<<=**|左移指派|Binary|
|**<=**|小於或等於|Binary|
|**=**|指派|Binary|
|**==**|等式|Binary|
|**>**|大於|Binary|
|**>=**|大於或等於|Binary|
|**>>**|右移|Binary|
|**>>=**|右移指派|Binary|
|**[ ]**|陣列註標|—|
|**^**|互斥 OR|Binary|
|**^=**|互斥 OR 指派|Binary|
|**&#124;**|位元包含 OR|Binary|
|**&#124;=**|位元包含 OR 指派|Binary|
|**&#124;&#124;**|邏輯 OR|Binary|
|**~**|一補數|一元 (Unary)|
|**`delete`**|刪除|—|
|**`new`**|新增|—|
|轉換運算子|轉換運算子|一元 (Unary)|

<sup>1</sup>兩個版本的一元遞增和遞減運算子存在：前置遞增和後置遞增。

如需詳細資訊，請參閱運算子多載的[一般規則](../cpp/general-rules-for-operator-overloading.md)。 多載運算子的各種分類限制描述於下列主題：

- [一元運算子](../cpp/overloading-unary-operators.md)

- [二元運算子](../cpp/binary-operators.md)

- [指派](../cpp/assignment.md)

- [函式呼叫](../cpp/function-call-cpp.md)

- [下標](../cpp/subscripting.md)

- [類別成員存取](../cpp/member-access.md)

- [遞增和遞減](../cpp/increment-and-decrement-operator-overloading-cpp.md)。

- [使用者定義型別轉換](../cpp/user-defined-type-conversions-cpp.md)

下表中顯示的運算子無法多載。 資料表包含預處理器符號 **#** 和 **##** 。

### <a name="nonredefinable-operators"></a>不可重新定義的運算子

|運算子|名稱|
|-|-|
|**.**|成員選取|
|**. &#42;**|成員指標選取|
|**::**|範圍解析|
|**? :**|條件式|
|**#**|前置處理器轉換成字串|
|**##**|前置處理器串連|

雖然多載運算子通常由編譯器在程式碼中遇到時隱含地呼叫，不過也能像任何成員或非成員函式呼叫一樣地明確叫用：

```cpp
Point pt;
pt.operator+( 3 );  // Call addition operator to add 3 to pt.
```

## <a name="example"></a>範例

下列範例會多載 **+** 運算子，以加入兩個複數並傳回結果。

```cpp
// operator_overloading.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct Complex {
   Complex( double r, double i ) : re(r), im(i) {}
   Complex operator+( Complex &other );
   void Display( ) {   cout << re << ", " << im << endl; }
private:
   double re, im;
};

// Operator overloaded using a member function
Complex Complex::operator+( Complex &other ) {
   return Complex( re + other.re, im + other.im );
}

int main() {
   Complex a = Complex( 1.2, 3.4 );
   Complex b = Complex( 5.6, 7.8 );
   Complex c = Complex( 0.0, 0.0 );

   c = a + b;
   c.Display();
}
```

```Output
6.8, 11.2
```

## <a name="in-this-section"></a>本節內容

- [運算子多載的一般規則](../cpp/general-rules-for-operator-overloading.md)

- [多載一元運算子](../cpp/overloading-unary-operators.md)

- [二元運算子](../cpp/binary-operators.md)

- [指派](../cpp/assignment.md)

- [函式呼叫](../cpp/function-call-cpp.md)

- [下標](../cpp/subscripting.md)

- [成員存取](../cpp/member-access.md)

## <a name="see-also"></a>另請參閱

[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
