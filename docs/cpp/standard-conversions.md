---
title: "標準轉換 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "轉換, 標準"
  - "左值"
  - "標準轉換, 的分類"
ms.assetid: ce7ac8d3-5c99-4674-8229-0672de05528d
caps.latest.revision: 10
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 標準轉換
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 語言定義其基本類型之間的轉換。  同時定義指標、參考及成員指標衍生類型的轉換。  這些轉換稱為「標準轉換」\(如需類型、標準類型和衍生類型的詳細資訊，請參閱[類型](http://msdn.microsoft.com/zh-tw/6882ee83-ea32-4373-8d57-c3efbbc15af0)\)。  
  
 本節將討論下列標準轉換：  
  
-   [整數提升](../misc/integral-promotions.md)  
  
-   [整數轉換](../misc/integral-conversions.md)  
  
-   [浮動轉換](../misc/floating-conversions.md)  
  
-   [浮動和整數轉換](../misc/floating-and-integral-conversions.md)  
  
-   [算術轉換](../misc/arithmetic-conversions.md)  
  
-   [指標轉換](../misc/pointer-conversions-cpp.md)  
  
-   [參考轉換](../misc/reference-conversions.md)  
  
-   [成員指標轉換](../misc/pointer-to-member-conversions.md)  
  
    > [!NOTE]
    >  使用者定義的類型可以自行指定其轉換。  [建構函式](../cpp/constructors-cpp.md)和[轉換](../cpp/user-defined-type-conversions-cpp.md)中都會探討使用者定義類型的轉換。  
  
 下列程式碼會引發轉換 \(本範例是整數提升\)：  
  
```  
long  lnum1, lnum2;  
int   inum;  
  
// inum promoted to type long prior to assignment.  
lnum1 = inum;  
  
// inum promoted to type long prior to multiplication.  
lnum2 = inum * lnum2;  
```  
  
> [!NOTE]
>  必須產生參考類型，轉換結果才會是左值。  例如，使用者定義的轉換宣告為  
  
```  
operator int&()  
```  
  
> [!NOTE]
>  會傳回參考且為左值。  不過，轉換宣告為  
  
```  
operator int()  
```  
  
> [!NOTE]
>  則會傳回物件且不是左值。  
  
## 整數提升  
 整數類資料類型的物件可以轉換成另一種範圍更廣的整數類資料類型 \(也就是可代表一組更大範圍值的類型\)。  這種擴展的轉換類型稱為「整數提升」。 整數提升可在能夠使用另一種整數類資料類型時，讓您在運算式中使用下列項目：  
  
-   `char` 和 `short int` 類型的物件、常值和常數  
  
-   列舉類型  
  
-   `int` 位元欄位  
  
-   列舉值  
  
 C\+\+ 提升為「保留值」。 也就是說，保證提升後的值會和提升之前的值一樣。  在保留值的提升中，較短的整數類資料類型物件 \(例如 `char` 類型的位元欄位或物件\) 會提升為 `int` 類型 \(如果 `int` 能夠代表原始類型的完整範圍\)。  如果 `int` 無法代表值的完整範圍，則物件會提升為 `unsigned int` 類型。  雖然這種策略與 ANSI C 所使用的策略相同，但是保留值的轉換不會保留物件的正負號狀態。  
  
 保留值的提升和保留正負號狀態的提升通常會產生相同的結果。  不過，如果提升的物件是下列其中一項，則兩者可能會產生不同的結果：  
  
-   **\/**、`%`、`/=`、`%=`、**\<**、**\<\=**、**\>** 或 **\>\=** 的運算元  
  
     這些運算子需要依據正負號判斷結果。  因此，保留值和保留正負號的提升套用至這些運算元時，會產生不同的結果。  
  
-   **\>\>** 或 **\>\>\=** 的左運算元  
  
     執行移位作業時，這些運算子會將帶正負號和不帶正負號的數量視為不同。  對於帶正負號的數量，將數量右移會造成正負號位元傳播至空出的位元位置。  對於不帶正負號的數量，空出的位元位置會以零填滿。  
  
-   多載函式的引數，或是依據運算元類型的正負號狀態進行引數比對的多載運算子之運算元   \(如需定義多載運算子的詳細資訊，請參閱[多載運算子](../cpp/operator-overloading.md)\)。  
  
## 整數轉換  
 整數轉換是在整數類資料類型之間執行。  整數類資料類型包括 `char`、`int` 和 **long** \(以及這些類型的 **short**、**signed** 和 `unsigned` 版本\)。  
  
 **帶正負號到不帶正負號**  
  
 帶正負號整數類型的物件可以轉換成對應的不帶正負號的類型。  當這些轉換發生時，實際的位元模式不會改變，不過資料的解譯會改變。  請參考下列程式碼：  
  
```  
// conve__pluslang_Converting_Signed_to_Unsigned.cpp  
// compile with: /EHsc  
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
  
 上述範例中定義了 `signed short`、`i` 並將其初始化為負數。  `(u = i)` 運算式會使得 `i` 先轉換成 **unsigned short** 再指派給 `u`。  
  
 **不帶正負號到帶正負號**  
  
 不帶正負號整數類資料類型的物件可以轉換成對應的帶正負號資料類型。  不過，如果不帶正負號的物件的值超出可由帶正負號類型表示的範圍，這種轉換可能會造成資料的錯譯，如下列範例所示：  
  
```  
// conve__pluslang_Converting_Unsigned_to_Signed.cpp  
// compile with: /EHsc  
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
  
 在前述範例中，`u` 是一個 `unsigned` **short** 整數類物件，必須轉換成帶正負號的數量，以評估 `(i = u)` 運算式。  因為其值無法以 `signed short` 適當地表示，因此會造成資料錯譯，如下所示。  
  
## 浮點轉換  
 浮動類型的物件可以安全地轉換為更精確的浮動類型，也就是說，轉換時不會遺失精確度。  例如，從 **float** 轉換到 **double**，或從 **double** 轉換到 `long double` 是安全的，因此其值不變。  
  
 如果其範圍可由該類型表示，則浮動類型的物件可以轉換為較不精確的類型。  \(如需浮動類型的範圍，請參閱[浮動限制](../cpp/floating-limits.md)\)。 如果無法精確地表示原始值，可以將它轉換為下一個較高或下一個較小的可表示值。  如果這個值不存在，則結果會是未定義。  參考下列範例：  
  
```  
cout << (float)1E300 << endl;  
```  
  
 **float** 類型可以表示的最大值為 3.402823466E38，它是比 1E300 小很多的數字。  因此，該數字會轉換為無限大，而結果會是 1.\#INF。  
  
## 整數與浮點類型之間的轉換  
 某些運算式可能會導致浮點類型的物件轉換成整數類型，反之亦然。  當整數類資料類型的物件轉換成浮點類型，且原始值無法正確表示時，結果會是下一個較大或較小的可顯示值。  
  
 當浮動類型的物件轉換為整數類資料類型時，會將小數部分截斷。  在轉換過程中不會進行四捨五入。  截斷表示會將一個如 1.3 的數字轉換成 1，而 –1.3 則會轉換為 –1。  
  
## 算術轉換  
 許多二元運算子 \(在[以二元運算子構成的運算式](../cpp/expressions-with-binary-operators.md)中討論\) 會導致運算元的轉換，並以相同的方式產生結果。  導致這些運算子進行轉換的方式稱為「一般算術轉換」。 針對不同原生類型的運算元執行算術轉換如下表所示。  Typedef 類型是根據其基礎原生類型而運作。  
  
### 類型轉換的條件  
  
|符合條件|轉換|  
|----------|--------|  
|任一個運算元的類型為 **long double**。|其他運算元會轉換為類型 **long double**。|  
|不符合上述條件，且任一個運算元的類型為 **double**。|其他運算元會轉換為 **double**。|  
|不符合上述條件，且任一個運算元的類型為 **float**。|其他運算元會轉換為 **float**。|  
|不符合上述條件 \(所有運算元都不是浮動類型\)。|在運算元上執行整數提升如下：<br /><br /> -   如果任一運算元的類型是 `unsigned` **long**，就會將另一個運算元轉換成 `unsigned long` 類型。<br />-   如果不符合上述條件，並且任一運算元的類型為 **long**，而另一個運算元的類型為 `unsigned` `int`，則會將兩個運算元都轉換成 `unsigned long` 類型。<br />-   如果不符合上述兩個條件，而且任一運算元的類型為 **long**，就會將另一個運算元轉換成 **long** 類型。<br />-   如果不符合上述三個條件，而且任一運算元的類型是 `unsigned int`，則會將另一個運算元轉換成 `unsigned int` 類型。<br />-   如果不符合上述任何條件，則會將兩個運算元都轉換成 `int` 類型。|  
  
 下列程式碼說明表格中所述的這些轉換規則：  
  
```  
// arithmetic_conversions.cpp  
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
  
 在上述範例中的第一個陳述式會顯示兩個整數類資料類型 \(`iVal` 和 `ulVal`\) 的乘法。  符合的條件為兩個運算元都不是浮動類型，以及其中一個運算元的類型為 `unsigned int`。  因此，其他運算元 \(`iVal`\) 會轉換為 `unsigned int` 類型。  此結果會指派給 `dVal`。  符合的條件是其中一個運算元為類型 **double**，因此，`unsigned int` 相乘的結果會轉換成 **double** 類型。  
  
 上述範例中的第二個陳述式顯示 **float** 和整數資料類型 \(`fVal` 和 `ulVal`\) 的加法。  `ulVal` 變數會轉換成 **float** \(資料表中的第三個條件\)。  加法的結果會轉換成 **double** 類型 \(資料表中的第二個條件\) 並指派給 `dVal`。  
  
## 指標轉換  
 在執行指派、初始化、比較和其他運算式時，可以轉換指標。  
  
### 類別的指標  
 在兩種情況下，類別的指標可以轉換成基底類別的指標。  
  
 第一種情況是可存取指定的基底類別，而且轉換明確。  \(如需模稜兩可之基底類別參考的詳細資訊，請參閱[多個基底類別](../cpp/multiple-base-classes.md)\)。  
  
 基底類別是否可存取，取決於衍生中所使用的繼承種類。  請參考下圖中說明的繼承。  
  
 ![顯示基底類別存取範圍的繼承圖形](../cpp/media/vc38xa1.png "vc38XA1")  
說明基底類別存取範圍的繼承圖表  
  
 下表說明圖中所示情況的基底類別存取範圍。  
  
### 基底類別存取範圍  
  
|函式類型|衍生|從<br /><br /> B\* 轉換成 A\* 是否合法?|  
|----------|--------|-----------------------------|  
|外部 \(非類別範圍\) 函式|Private|否|  
||Protected|否|  
||Public|是|  
|B 成員函式 \(B 範圍中\)|Private|是|  
||Protected|是|  
||Public|是|  
|C 成員函式 \(C 範圍中\)|Private|否|  
||Protected|是|  
||Public|是|  
  
 類別指標可以轉換成基底類別指標的第二種情況，是使用明確類型轉換   \(如需明確類型轉換的詳細資訊，請參閱[使用明確類型轉換的運算式](http://msdn.microsoft.com/zh-tw/060ad6b4-9592-4f3e-8509-a20ac84a85ae)\)。  
  
 這類轉換的結果會是「子物件」指標，也就是物件中以基底類別完整描述的部分。  
  
 下列程式碼會定義兩種類別 `A` 和 `B`，其中 `B` 衍生自 `A` \(如需繼承的詳細資訊，請參閱[衍生類別](../cpp/inheritance-cpp.md)\)。 然後它會定義 `bObject`、`B` 類型的物件，以及兩個指向物件的指標 \(`pA` 和 `pB`\)。  
  
```  
// conve__pluslang_Pointers_to_Classes.cpp  
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
  
 `pA` 指標是 `A *` 類型，可以解譯為表示「`A` 類型物件的指標」。 `bObject` 的成員 `(`例如 `BComponent` 和 `BMemberFunc`\) 對於 `B` 類型是唯一的，因此無法透過 `pA` 存取。  `pA` 指標只允許存取 `A` 類別中定義的那些物件特性 \(成員函式和資料\)。  
  
### 函式的指標  
 如果類型 **void \*** 的大小足以保留函式的指標，即可將該指標轉換為類型 **void \***。  
  
### void 的指標  
 `void` 類型的指標可以轉換為任何其他類型的指標，但必須使用明確的類型轉換 \(不同於 C\)   \(如需類型轉換的詳細資訊，請參閱[使用明確類型轉換的運算式](http://msdn.microsoft.com/zh-tw/060ad6b4-9592-4f3e-8509-a20ac84a85ae)\)。 任何類型的指標可以隱含地轉換成類型 `void` 的指標。類型不完整之物件的指標可以轉換為 `void` \(隱含\) 和反向轉換 \(明確\)。  這類轉換的結果等於原始指標的值。  若物件宣告後，沒有足夠的資訊可用來判斷其大小和基底類別，則會將該物件視為不完整。  
  
 不是 **const** 或 `volatile` 之任何物件的指標都可以隱含轉換成 **void \*** 類型的指標。  
  
### const 和 volatile 指標  
 C\+\+ 不提供從 **const** 或 `volatile` 類型標準轉換為非 **const** 或 `volatile` 的類型。  不過，使用明確類型轉型 \(包括不安全的轉換\) 即可指定任何類型的轉換。  
  
> [!NOTE]
>  C\+\+ 成員指標 \(靜態成員指標除外\) 不同於一般指標，而且沒有相同的標準轉換。  靜態成員的指標是一般指標，具有與一般指標相同的轉換。  \(如需詳細資訊，請參閱[\(NOTINBUILD\) Directly Derived Types](http://msdn.microsoft.com/zh-tw/d2d611d1-dbff-4fb4-9858-e1572544f5c3)。\)  
  
### null 指標轉換  
 判斷值為零的整數常數運算式，或轉換為指標型別的運算式會轉換成稱為「null 指標」的指標。 這個指標保證與任何有效物件或函式的指標不相等 \(除了以物件為主的指標以外，這些指標可能會內含相同的位移，並且仍然指向不同的物件\)。  
  
 在 C\+\+11 中，[nullptr](../cpp/nullptr.md) 類型應該最好是 C 樣式 null 指標。  
  
### 指標運算式轉換  
 具有陣列類型的任何運算式都可以轉換成相同類型的指標。  轉換的結果是第一個陣列元素的指標。  下列範例將示範這類轉換：  
  
```  
char szPath[_MAX_PATH]; // Array of type char.  
char *pszPath = szPath; // Equals &szPath[0].  
```  
  
 導致函式傳回特殊類型的運算式會轉換成傳回該類型之函式的指標，但下列情形例外：  
  
-   運算式做為傳址運算子 \(**&**\) 的運算元。  
  
-   運算式做為函式呼叫運算子的運算元。  
  
## 參考轉換  
 在下列情況下，類別的參考可以轉換成基底類別的參考：  
  
-   指定的基底類別是可存取的 \(如[類別的指標](../misc/pointers-to-classes.md)中所定義\)。  
  
-   轉換不可以模稜兩可。  \(如需模稜兩可之基底類別參考的詳細資訊，請參閱[多個基底類別](../cpp/multiple-base-classes.md)\)。  
  
 轉換的結果是表示基底類別子物件的指標。  
  
## 成員的指標  
 在執行指派、初始化、比較和其他運算式時，可以轉換類別成員的指標。  本節將描述下列成員指標的轉換：  
  
## 基底類別成員的指標  
 當下列條件符合時，就可以將基底類別成員的指標轉換為從其衍生之類別成員的指標：  
  
-   反向轉換 \(即從衍生類別的指標轉換為基底類別指標\) 是可以存取的。  
  
-   衍生的類別無法由基底類別進行虛擬繼承。  
  
 當左運算元為成員的指標時，右運算元必須是成員指標類型，或者必須是判斷值為 0 的常數運算式。  這項指派只在下列情況下有效：  
  
-   右運算元為與左運算元相同類別的成員指標。  
  
-   左運算元是一種公開且明確地從右運算元類別所衍生的類別成員指標。  
  
## 整數常數轉換  
 運算結果為零的整數常數運算式會轉換成「Null 指標」。 這個指標保證與任何有效物件或函式的指標不相等 \(除了以物件為主的指標以外，這些指標可能會內含相同的位移，並且仍然指向不同的物件\)。  
  
 下列程式碼說明在 `i` 類別中針對成員 `A` 所定義的指標。  指標 \(即 `pai`\) 已初始化為 0，為 Null 指標。  
  
```  
// conve__pluslang_Integral_Constant_Expressions.cpp  
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
  
## 請參閱  
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)