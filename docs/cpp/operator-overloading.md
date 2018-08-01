---
title: 運算子多載 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- operator_cpp
- operator
dev_langs:
- C++
helpviewer_keywords:
- redefinable operators [C++]
- non-redefinable operators [C++]
- operator keyword [C++]
- operators [C++], overloading
- operator overloading
ms.assetid: 56ad4c4f-dd0c-45e0-adaa-08fe98cb1f8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eae4b7cc2211462b097efbefca580b796d573c59
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408943"
---
# <a name="operator-overloading"></a>運算子多載

**運算子**關鍵字會宣告函式，指定什麼*運算子符號*表示套用至類別的執行個體時。 這讓運算子有多個意義，或稱為「多載」。 編譯器會檢查運算元的類型，以區別運算子的不同意義。

## <a name="syntax"></a>語法

> *型別***運算子***運算子符號* **(** *參數清單* **)**

## <a name="remarks"></a>備註

您可以用全域方式或以逐一類別為基礎，重新定義大多數內建運算子的函式。 多載運算子實做為函式。

多載運算子的名稱是**運算子** *x*，其中*x*是運算子下, 表中所顯示的樣子。 比方說，若要多載加法運算子，您要定義呼叫的函式**operator +**。 同樣地，若要多載加法/指派運算子中， **+=**，定義呼叫的函式**operator + =**。

### <a name="redefinable-operators"></a>可重新定義的運算子

|運算子|名稱|類型|
|--------------|----------|----------|
|**、**|逗號|二元|
|**!**|邏輯 NOT|一元|
|**\!=**|不等|二元|
|**%**|模數|二元|
|**%=**|模數指派|二元|
|**&**|位元 AND|二元|
|**&**|傳址|一元|
|**&&**|邏輯 AND|二元|
|**&=**|位元 AND 指派|二元|
|**( )**|函式呼叫 |—|
|**( )**|轉型運算子|一元|
|**&#42;**|乘法|二元|
|**&#42;**|指標取值 (Dereference)|一元|
|**&#42;=**|乘法指派|二元|
|**+**|加入|二元|
|**+**|一元加號|一元|
|**++**|遞增<sup>1</sup>|一元|
|**+=**|加法指派|二元|
|**-**|減法|二元|
|**-**|一元負運算|一元|
|**--**|遞減<sup>1</sup>|一元|
|**-=**|減法指派|二元|
|**->**|成員選取|二元|
|**->&#42;**|成員指標選取|二元|
|**/**|除法|二元|
|**/=**|除法指派|二元|
|**\<**|小於|二元|
|**<<**|左移|二元|
|**<<=**|左移指派|二元|
|**<=**|小於或等於|二元|
|**=**|指派|二元|
|**==**|相等|二元|
|**>**|大於|二元|
|**>=**|大於或等於|二元|
|**>>**|右移|二元|
|**>>=**|右移指派|二元|
|**[ ]**|陣列註標|—|
|**^**|互斥 OR|二元|
|**^=**|互斥 OR 指派|二元|
|**&#124;**|位元包含 OR|二元|
|**&#124;=**|位元包含 OR 指派|二元|
|**&#124;&#124;**|邏輯 OR|二元|
|**~**|一補數|一元|
|**delete**|刪除|—|
|**new**|新增|—|
|轉換運算子|轉換運算子|一元|

<sup>1</sup>兩個版本的一元遞增和遞減運算子存在： 前置遞增和後置遞增。

請參閱[運算子多載的一般規則](../cpp/general-rules-for-operator-overloading.md)如需詳細資訊。 多載運算子的各種分類限制描述於下列主題：

- [一元運算子](../cpp/overloading-unary-operators.md)

- [二元運算子](../cpp/binary-operators.md)

- [指派](../cpp/assignment.md)

- [函式呼叫](../cpp/function-call-cpp.md)

- [註標](../cpp/subscripting.md)

- [類別成員存取](../cpp/member-access.md)

- [遞增和遞減](../cpp/increment-and-decrement-operator-overloading-cpp.md)。

- [使用者定義類型轉換](../cpp/user-defined-type-conversions-cpp.md)

下表中顯示的運算子無法多載。 資料表包含的前置處理器符號**#** 並**##**。

### <a name="nonredefinable-operators"></a>不可重新定義的運算子

|運算子|名稱|
|-|-|
|**.**|成員選取|
|**.&#42;**|成員指標選取|
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

下列範例會多載**+** 運算子，將兩個複數相加，並傳回結果。

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

- [註標](../cpp/subscripting.md)

- [成員存取](../cpp/member-access.md)

## <a name="see-also"></a>另請參閱
 [C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)  
 [關鍵字](../cpp/keywords-cpp.md)