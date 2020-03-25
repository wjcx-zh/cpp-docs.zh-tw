---
title: 標準轉換
ms.date: 10/02/2019
helpviewer_keywords:
- standard conversions, categories of
- L-values [C++]
- conversions, standard
ms.assetid: ce7ac8d3-5c99-4674-8229-0672de05528d
ms.openlocfilehash: 41ad348b7109451f519c44f685cea0a271f71925
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161006"
---
# <a name="standard-conversions"></a>標準轉換

C++ 語言定義其基本類型之間的轉換。 同時定義指標、參考及成員指標衍生類型的轉換。 這些轉換稱為*標準轉換*。

本節將討論下列標準轉換：

- 整數提升

- 整數轉換

- 浮動轉換

- 浮動和整數轉換

- 算術轉換

- 指標轉換

- 參考轉換

- 成員指標轉換

  > [!NOTE]
  > 使用者定義的類型可以自行指定其轉換。 使用者定義[類型的轉換會涵蓋在函](../cpp/constructors-cpp.md)式和[轉換](../cpp/user-defined-type-conversions-cpp.md)中。

下列程式碼會引發轉換 (本範例是整數提升)：

```cpp
long  long_num1, long_num2;
int   int_num;

// int_num promoted to type long prior to assignment.
long_num1 = int_num;

// int_num promoted to type long prior to multiplication.
long_num2 = int_num * long_num2;
```

必須產生參考類型，轉換結果才會是左值。 例如，宣告為 `operator int&()` 的使用者定義轉換會傳回參考，而且是左值。 不過，宣告為 `operator int()` 的轉換會傳回物件，而不是左值。

## <a name="integral-promotions"></a>整數提升

整數類資料類型的物件可以轉換成另一個較大的整數類型，也就是可以代表一組大型值的類型。 這種擴展類型的轉換稱為「*整數提升*」。 使用整數提升時，您可以在運算式中使用下列類型，其中可以使用另一個整數類型：

- **Char**和**short int**類型的物件、常值和常數

- 列舉型別

- **int**位欄位

- 列舉值

C++升級為「保留值」，因為在回復後的值保證會與升級前的值相同。 在保留值的升級中，較短整數類型的物件（例如， **char**類型的位欄位或物件）會升級為**int**類型（如果**int**可以代表原始類型的完整範圍）。 如果**int**不能代表完整的值範圍，則物件會升級為類型不**帶正負**號的 int。 雖然這項策略與標準 C 所使用的策略相同，但保留值的轉換不會保留物件的 "正負號狀態"。

保留值的提升和保留正負號狀態的提升通常會產生相同的結果。 不過，如果提升的物件顯示為，它們可能會產生不同的結果：

- `/`、`%`、`/=`、`%=`、`<`、`<=`、`>`或 `>=` 的運算元

   這些運算子需要依據正負號判斷結果。 在套用到這些運算元時，保留值和簽署的升級會產生不同的結果。

- `>>` 或 `>>=` 的左運算元

   這些運算子會在 shift 作業中以不同的方式來處理帶正負號和未簽署的數量 對於帶正負號的數量，右移作業會將符號位傳播到空出的位位置，而空出的位位置則會以不帶正負號的數量填入零。

- 多載函式的引數，或多載運算子的運算元，這取決於引數比對的運算元類型正負號狀態。 如需定義多載運算子的詳細資訊，請參閱多載[運算子](../cpp/operator-overloading.md)。

## <a name="integral-conversions"></a>整數轉換

*整數轉換*是整數類資料類型之間的轉換。 整數類資料類型**為 char**、 **short** （或**short int**）、 **int**、 **long**和**long long**。 這些類型可能會以**帶正負**號或不帶**正負**號的方式限定，而且不帶**正負**號的可做為不**帶正負號 int**

### <a name="signed-to-unsigned"></a>帶正負號到不帶正負號

帶正負號整數類型的物件可以轉換成對應的不帶正負號的類型。 當這些轉換發生時，實際的位模式不會變更。 不過，資料的轉譯也會變更。 請參考下列程式碼：

```cpp
#include <iostream>

using namespace std;
int main()
{
    short  i = -3;
    unsigned short u;

    cout << (u = i) << "\n";
}
// Output: 65533
```

在上述範例中，會定義帶正負號的**short**、`i`，並將其初始化為負數。 運算式 `(u = i)` 會導致 `i` 在指派給 `u`之前，轉換成不**帶正負**號的簡短。

### <a name="unsigned-to-signed"></a>不帶正負號到帶正負號

不帶正負號整數類資料類型的物件可以轉換成對應的帶正負號資料類型。 不過，如果不帶正負號的值不在帶正負號類型的可顯示範圍內，則結果不會有正確的值，如下列範例所示：

```cpp
#include <iostream>

using namespace std;
int main()
{
short  i;
unsigned short u = 65533;

cout << (i = u) << "\n";
}
//Output: -3
```

在上述範例中，`u` 是不**帶正負**號的短整數物件，必須轉換成帶正負號的數量，以評估運算式 `(i = u)`。 因為其值無法在**帶正負**號的簡短情況下正確表示，所以會以顯示的方式來誤解資料。

## <a name="floating-point-conversions"></a>浮點轉換

浮動類型的物件可以安全地轉換為更精確的浮動類型，也就是說，轉換時不會遺失精確度。 例如，從**float**轉換為**double** ，或從**double**轉換成**long double**是安全的，且值不變。

浮動類型的物件也可以轉換成較不精確的類型（如果它是在該類型所表示的範圍內）。 （如需浮動類型的範圍，請參閱[浮動限制](../cpp/floating-limits.md)）。如果原始值無法精確地表示，則可以轉換成下一個較高或下一個較低的可顯示值。 如果沒有這樣的值，則會產生未定義的結果。 請考慮下列範例：

```cpp
cout << (float)1E300 << endl;
```

**Float**類型所表示的最大值是 3.402823466 3.402823 e 38-比1E300 更小的數位。 因此，數位會轉換成無限大，而結果會是 "inf"。

## <a name="conversions-between-integral-and-floating-point-types"></a>整數與浮點類型之間的轉換

某些運算式可能會導致浮點類型的物件轉換成整數類型，反之亦然。 當整數類資料類型的物件轉換成浮點類型，且原始值無法精確地表示時，結果會是下一個較高或下一個較低的可顯示值。

當浮動類型的物件轉換成整數類資料類型時，分數部分會被*截斷*，或四捨五入到零。 例如1.3 的數位會轉換成1，而-1.3 會轉換為-1。 如果截斷的值高於最大可表示的值，或小於最小的可顯示值，則結果為未定義。

## <a name="arithmetic-conversions"></a>算術轉換

許多二元運算子（在[具有二元運算子的運算式](../cpp/expressions-with-binary-operators.md)中討論）會導致運算元的轉換，並以相同的方式產生結果。 這些運算子的轉換會被稱為*一般算術轉換*。 具有不同原生類型之運算元的算術轉換會依照下表所示完成。 Typedef 類型是根據其基礎原生類型而運作。

### <a name="conditions-for-type-conversion"></a>類型轉換的條件

|符合條件|轉換|
|--------------------|----------------|
|任一個運算元的類型為**long double**。|其他運算元會轉換成**long double**類型。|
|不符合上述條件，且任一個運算元的類型為**double**。|其他運算元會轉換為**double**類型。|
|不符合上述條件，而且任一運算元的類型為**float**。|其他運算元會轉換為**float**類型。|
|不符合上述條件 (所有運算元都不是浮動類型)。|運算元會取得整數提升，如下所示：<br /><br />-如果任一個運算元的類型不**帶正負**號，則會將另一個運算元轉換成不**帶正負**號的 long 類型。<br />-如果不符合上述條件，而且任一運算元的類型是**long** ，而另一個是不**帶正負**號的整數類型，這兩個運算元都會轉換成不**帶正負**號的 long 類型。<br />-如果不符合上述兩個條件，而且任一運算元的類型是**long**，則會將另一個運算元轉換成**long**類型。<br />-如果不符合上述三個條件，而且任一運算元的類型不**帶正負**號，則會將另一個運算元轉換成不**帶正負**號的整數類型。<br />-如果未符合上述任何條件，則會將兩個運算元轉換成**int**類型。|

下列程式碼說明表格中所述的這些轉換規則：

```cpp
double dVal;
float fVal;
int iVal;
unsigned long ulVal;

int main() {
   // iVal converted to unsigned long
   // result of multiplication converted to double
   dVal = iVal * ulVal;

   // ulVal converted to float
   // result of addition converted to double
   dVal = ulVal + fVal;
}
```

在上述範例中的第一個陳述式會顯示兩個整數類資料類型 (`iVal` 和 `ulVal`) 的乘法。 符合的條件為兩個運算元都不是浮動類型，而一個運算元的類型不是不**帶正負**號的 int。因此，另一個運算元（`iVal`）會轉換成不**帶正負**號的 int 型別。然後會將結果指派給 `dVal`。 這裡符合的條件是一個運算元的類型為**double**，因此乘法的不**帶正負號 int**結果會轉換成**double**類型。

前述範例中的第二個語句會顯示**float**和整數類資料類型的加法： `fVal` 和 `ulVal`。 `ulVal` 變數會轉換成**float**類型（資料表中的第三個條件）。 加法的結果會轉換成**double**類型（資料表中的第二個條件），並指派給 `dVal`。

## <a name="pointer-conversions"></a>指標轉換

在執行指派、初始化、比較和其他運算式時，可以轉換指標。

### <a name="pointer-to-classes"></a>類別的指標

在兩種情況下，類別的指標可以轉換成基底類別的指標。

第一種情況是可存取指定的基底類別，而且轉換明確。 如需不明確的基類參考的詳細資訊，請參閱[多個基類](../cpp/multiple-base-classes.md)。

基底類別是否可存取，取決於衍生中所使用的繼承種類。 請參考下圖中說明的繼承。

![顯示基類&#45;存取範圍的繼承圖](../cpp/media/vc38xa1.gif "顯示基類&#45;存取範圍的繼承圖") <br/>
說明基底類別存取範圍的繼承圖表

下表說明圖中所示情況的基底類別存取範圍。

|函式類型|衍生|從<br /><br /> B * 到\* 法律？|
|----------------------|----------------|-------------------------------------------|
|外部 (非類別範圍) 函式|Private|否|
||受保護|否|
||公開|是|
|B 成員函式 (B 範圍中)|Private|是|
||受保護|是|
||公開|是|
|C 成員函式 (C 範圍中)|Private|否|
||受保護|是|
||公開|是|

類別指標可以轉換成基底類別指標的第二種情況，是使用明確類型轉換 如需明確類型轉換的詳細資訊，請參閱[明確類型轉換運算子](explicit-type-conversion-operator-parens.md)。

這類轉換的結果是子*物件的指標，這*是由基類完整描述的物件部分。

下列程式碼會定義兩種類別 `A` 和 `B`，其中 `B` 衍生自 `A` （如需繼承的詳細資訊，請參閱[衍生類別](../cpp/inheritance-cpp.md)）。然後，它會定義 `bObject`、`B`類型的物件，以及指向物件的兩個指標（`pA` 和 `pB`）。

```cpp
// C2039 expected
class A
{
public:
    int AComponent;
    int AMemberFunc();
};

class B : public A
{
public:
    int BComponent;
    int BMemberFunc();
};
int main()
{
   B bObject;
   A *pA = &bObject;
   B *pB = &bObject;

   pA->AMemberFunc();   // OK in class A
   pB->AMemberFunc();   // OK: inherited from class A
   pA->BMemberFunc();   // Error: not in class A
}
```

`pA` 指標是 `A *` 類型，可以解譯為表示「`A` 類型物件的指標」。 `bObject` 的成員（例如 `BComponent` 和 `BMemberFunc`）對於類型 `B` 而言是唯一的，因此無法透過 `pA`存取。 `pA` 指標只允許存取 `A` 類別中定義的那些物件特性 (成員函式和資料)。

### <a name="pointer-to-function"></a>函式的指標

如果類型 `void *` 夠大，足以容納該指標，則函式的指標可以轉換成類型 `void *`。

### <a name="pointer-to-void"></a>void 的指標

類型**void**的指標可以轉換成任何其他類型的指標，但只能使用明確類型轉換（不同于 C）。 任何類型的指標都可以隱含地轉換成**void**類型的指標。 類型之不完整物件的指標可以轉換成**void** （隱含）和 back （明確）的指標。 這類轉換的結果等於原始指標的值。 如果物件已宣告，但沒有足夠的可用資訊來判斷其大小或基類，則會將它視為不完整。

任何不是**const**或**volatile**之物件的指標都可以隱含地轉換成 `void *`類型的指標。

### <a name="const-and-volatile-pointers"></a>const 和 volatile 指標

C++不會提供從**const**或**volatile**類型到不是**const**或**volatile**類型的標準轉換。 不過，使用明確類型轉型 (包括不安全的轉換) 即可指定任何類型的轉換。

> [!NOTE]
> C++成員的指標（靜態成員指標除外）與一般指標不同，而且沒有相同的標準轉換。 靜態成員的指標是一般指標，具有與一般指標相同的轉換。

### <a name="null-pointer-conversions"></a>null 指標轉換

評估為零的整數常數運算式，或轉換成指標類型的運算式會轉換成稱為*null 指標*的指標。 這個指標一律會比較不等於任何有效物件或函式的指標。 例外狀況是物件的指標，可以具有相同的位移，而且仍然指向不同的物件。

在 c + + 11 中， [nullptr](../cpp/nullptr.md)類型應該慣用於 C 樣式的 null 指標。

### <a name="pointer-expression-conversions"></a>指標運算式轉換

具有陣列類型的任何運算式都可以轉換成相同類型的指標。 轉換的結果是第一個陣列元素的指標。 下列範例將示範這類轉換：

```cpp
char szPath[_MAX_PATH]; // Array of type char.
char *pszPath = szPath; // Equals &szPath[0].
```

導致函式傳回特殊類型的運算式會轉換成傳回該類型之函式的指標，但下列情形例外：

- 運算式用來做為傳址運算子（ **&** ）的運算元。

- 運算式做為函式呼叫運算子的運算元。

## <a name="reference-conversions"></a>參考轉換

在這些情況下，可以將類別的參考轉換為基類的參考：

- 可存取指定的基類。

- 轉換不可以模稜兩可。 （如需不明確的基類參考的詳細資訊，請參閱[多個基類](../cpp/multiple-base-classes.md)）。

轉換的結果是表示基底類別子物件的指標。

## <a name="pointer-to-member"></a>成員的指標

在執行指派、初始化、比較和其他運算式時，可以轉換類別成員的指標。 本節將描述下列成員指標的轉換：

### <a name="pointer-to-base-class-member"></a>基底類別成員的指標

當下列條件符合時，就可以將基底類別成員的指標轉換為從其衍生之類別成員的指標：

- 反向轉換 (即從衍生類別的指標轉換為基底類別指標) 是可以存取的。

- 衍生的類別無法由基底類別進行虛擬繼承。

當左運算元為成員的指標時，右運算元必須是成員指標類型，或者必須是判斷值為 0 的常數運算式。 這項指派只在下列情況下有效：

- 右運算元為與左運算元相同類別的成員指標。

- 左運算元是一種公開且明確地從右運算元類別所衍生的類別成員指標。

### <a name="null-pointer-to-member-conversions"></a>成員轉換的 null 指標

評估為零的整數常數運算式會轉換成 null 指標。 這個指標一律會比較不等於任何有效物件或函式的指標。 例外狀況是物件的指標，可以具有相同的位移，而且仍然指向不同的物件。

下列程式碼說明在 `i` 類別中針對成員 `A` 所定義的指標。 指標 (即 `pai`) 已初始化為 0，為 Null 指標。

```cpp
class A
{
public:
int i;
};

int A::*pai = 0;

int main()
{
}
```

## <a name="see-also"></a>另請參閱

[C++語言參考](../cpp/cpp-language-reference.md)
