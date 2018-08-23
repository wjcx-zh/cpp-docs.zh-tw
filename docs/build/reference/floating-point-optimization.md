---
title: Microsoft Visual c + + 浮點最佳化 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 082cd3a7721f1bc72899130159b724b292e5e217
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595044"
---
# <a name="microsoft-visual-c-floating-point-optimization"></a>Microsoft Visual c + + 浮點最佳化

取得最佳化浮點程式碼使用管理浮點語意的方法，Microsoft c + + 編譯器的控制代碼。 建立快速的程式，同時確保浮點程式碼會執行唯一安全的最佳化。

## <a name="optimization-of-floating-point-code-in-c"></a>C + + 中的浮點程式碼的最佳化

最佳化的 c + + 編譯器不只會將原始程式碼轉譯成機器碼，它排列機器指令，並提升效率及/或減少大小的方式。 不幸的是，許多常見的最佳化不是套用至計算浮點數時，一定是安全的。 一個很好的範例可以使用下列的總和演算法，David 錢、 」 功能每個電腦科學家應該知道有關浮點運算 」，從*運算 Surveys*、 年 3 月 1991 年以來，pg。 203:

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0, C=0, Y, T;
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = T;
   }
   return sum;
}
```

此函式會將 n**浮點數**陣列向量中的值`A`。 迴圈主體中，演算法會計算 「 更正 」 值，接著再套用下一個步驟的總和。 這個方法可大幅減少相較於簡單的總和，同時保留 o （n） 的時間複雜性的累計捨入錯誤。

貝氏 c + + 編譯器可能會假設，浮點算術會遵循相同的代數規則實數算術。 這類編譯器可能會錯誤地推斷，

> C = T-加總-Y = = > （總和 + Y）-加總-Y = = > 0;

也就是，C 的認知的值一律是常數的零。 如果此常數值，然後會傳播到後續的運算式，則會將迴圈主體減少以簡單的總和。 確切而言，

> Y = [i]-C = = > Y = [i]<br/>T = 總和 + Y = = > T = 總和 + A [i]<br/>sum = T = = > 總計 = 總計 + A [i]

因此，為了貝氏編譯器的邏輯轉換`KahanSum`函式會是：

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0; // C, Y & T are now unused
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

已轉換的演算法變快了，雖然*根本不是程式設計人員的意圖的精確表示*。 精巧的錯誤修正具有已全部移除，且我們會擁有簡單、 直接的總和演算法，其所有相關聯的錯誤。

當然，複雜的 c + + 編譯器會知道此代數規則的真實算術通常不適用於浮點算術。 不過，即使是複雜的 c + + 編譯器可能仍未正確解譯程式設計人員的意圖。

請考慮常見的最佳化，嘗試將保留在暫存器中的多個值，盡可能 (稱為 「 註冊 (enregistering) 」 值)。 在 `KahanSum`範例中，此最佳化可能會嘗試低落變數`C`，`Y`和`T`因為他們只在迴圈主體內的使用。 如果 52bits (double) 而不是 23bits （單一） 的註冊，有效位數，此最佳化有效型別會提升`C`，`Y`並`T`輸入**double**。 如果總和變數同樣不是機率，它仍會持續在單精確度編碼。 這會將轉換的語意`KahanSum`如下

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0;
   double C=0, Y, T; // now held in-register
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = (float) T;
   }
   return sum;
}
```

雖然`Y`，`T`並`C`現在計算的更高的精確度，這個新的編碼方式可能會產生較不精確的結果中的值而定`A[]`。 因此即使看似無害的最佳化可能會發生負面後果。

這類的最佳化問題並不限於 「 麻煩 」 的浮點程式碼。 當不正確地最佳化，甚至是簡單的浮點數演算法可能會失敗。 簡單、 直接總和的演算法，請考慮：

```cpp
float Sum( const float A[], int n )
{
   float sum=0;
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

因為某些浮點單位是能夠同時執行多個作業，編譯器可能會選擇參與的純量減少最佳化。 實際上，此最佳化會將簡單的 Sum 函數，從上方轉換成下列：

```cpp
float Sum( const float A[], int n )
{
   int n4 = n-n%4; // or n4=n4&(~3)
   int i;
   float sum=0, sum1=0, sum2=0, sum3=0;
   for (i=0; i<n4; i+=4)
   {
      sum = sum + A[i];
      sum1 = sum1 + A[i+1];
      sum2 = sum2 + A[i+2];
      sum3 = sum3 + A[i+3];
   }
   sum = sum + sum1 + sum2 + sum3;
   for (; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

此函式現在會維護四個不同的就，可以同時處理每個步驟。 雖然最佳化函式現在會快很多，最佳化的結果可能會與非最佳化的結果相當不同。 在進行這項變更，編譯器會假設關聯的浮點加法;也就是說，這些兩個運算式相等： `(a + b) + c == a + (b + c)`。 不過，關聯性不一定永遠成立的浮點數。 而不是計算總和為：

```cpp
sum = A[0]+A[1]+A[2]+...+A[n-1];
```

已轉換的函式現在會計算形式的結果

```cpp
sum = (A[0]+A[4]+A[8]+...)
    + (A[1]+A[5]+A[9]+...)
    + (A[2]+A[6]+A[10]+...)
    + (A[3]+A[7]+A[11]+...);
```

中的某些值`A[]`，加法運算的這個不同的順序，可能會產生非預期的結果。 若要進一步使事情更加複雜，某些程式設計人員可能會選擇預期這種最佳化，並適當地補償。 在此情況下，程式可以建構陣列`A`順序不同，因此最佳化的總和會產生預期的結果。 此外，在許多情況下可能是 「 關閉夠 」 最佳化結果的精確度。 當最佳化提供吸引人的速度優點時，這是特別有用。 視訊遊戲，比方說，需要更加速越好，但通常不需要高精確度的浮點數運算。 編譯器製作者，因此必須提供一種機制，來控制速度和精確度的通常不同目標的程式設計人員。

某些編譯器最佳化每個類型提供個別的交換器，以解決速度和精確性之間的權衡取捨。 這可讓開發人員，以停用造成變更其特定的應用程式的浮點精確度的最佳化。 雖然此方案可能提供較高程度的控制編譯器，它引入了數個額外的問題：

- 通常很清楚這會切換成啟用或停用。
- 停用任何單一最佳化可能會影響效能的非浮點程式碼。
- 每個額外的參數時，會產生許多新的參數組合;組合的數目很快會變得不便。

因此每個最佳化提供不同的交換器似乎吸引人，使用這類編譯器可能會很麻煩且不可靠。

提供許多 c + + 編譯器*一致性*浮點模型，(透過 **/Op**或是 **/fltconsistency**切換) 可讓開發人員建立程式相容使用嚴謹浮點語意。 當參與，此模型會防止編譯器在計算浮點數使用大部分的最佳化，同時允許這些最佳化的非浮點程式碼。 一致性模型，不過，有深側邊。 若要可預測的結果時傳回不同的 FPU 架構，幾乎所有實作 **/Op**捨入的中繼運算式，以使用者指定的有效位數; 例如，請考慮下列運算式：

```cpp
float a, b, c, d, e;
// . . .
a = b * c + d * e;
```

為了產生一致且可重複的結果，底下 **/Op**，這個運算式評估，如果已實作的如下所示：

```cpp
float x = b  *c;
float y = d * e;
a = x + y;
```

最後的結果現在會受到單精確度捨入錯誤*每個步驟中評估運算式*。 雖然此解譯絕對不會中斷任何 c + + 語意規則，就幾乎不會評估浮點運算式的最佳方式。 它是計算中繼結果方面甫的有效位數為過高通常更為理想。 比方說，它能以計算運算式`a = b * c + d * e`中做為在更高的精確度

```cpp
double x = b * c;
double y = d * e;
double z = x + y;
a = (float)z;
```

或更新版本

```cpp
long double x = b * c;
long double y = d * e
long double z = x + y;
a = (float)z;
```

在計算中更高的精確度的中繼結果，最終結果是大幅更精確。 諷刺，藉由採用的一致性模型，錯誤的可能性會增加時，使用者嘗試不安全的最佳化，藉以減少錯誤。 因此的一致性模型會嚴重降低效率同時提供更高的精確度不保證。 嚴重的數值程式設計師，這看起來很好的權衡取捨，而且是該模型不通常也收到的主要原因。

從版本 8.0 (C++® 2005)，Microsoft c + + 編譯器會提供更佳的替代方案。 它可讓程式設計人員可以選擇三種一般的浮點數模式之一： /fp: precise，/fp: fast 和 fp: strict。

- 下 fp： 精確，只能安全會執行最佳化浮點程式碼，而且不同於 **/Op**，最高的實際精確度一致的方式執行中繼的計算。
- /fp: fast 模式會放寬浮點數的規則，允許更積極的最佳化，但會犧牲精確度。
- /fp: strict 模式下提供所有一般的正確性的 fp： 精確同時啟用 fp 例外狀況語意，並防止不合法的轉換，且 FPU 環境變更 （例如變更到註冊的有效位數，捨入方向等）。

浮點例外狀況語意可以獨立控制命令列參數或編譯器 pragma;預設情況下，浮點例外狀況語意會停用下 fp： 精確且已啟用下 fp: strict。 編譯器也會提供控制 FPU 環境敏感度和特定浮點數的特定最佳化，例如縮寫。 這個簡單的模型為開發人員提供大量的編譯而不需要太多的編譯器參數的負擔或非預期的副作用的浮點程式碼的控制權。

## <a name="the-fpprecise-mode-for-floating-point-semantics"></a>Fp： 浮點語意的精確模式

預設的浮點語意模式是 fp： 精確。 選取此模式時，編譯器嚴格遵守一組安全性規則時最佳化浮點運算。 這些規則可讓編譯器產生有效率的電腦程式碼，同時維持計算浮點數的精確度。 為了方便快速的實際執行程式，fp： 精確的模型在 （雖然它們可以明確地啟用），會停用浮點例外狀況語意。 Microsoft 已選取 fp： 精確做為預設的浮點模式因為它會建立快速且正確的程式。

若要明確地要求 fp： 使用命令列編譯器，也就是使用的精確模式[/fp： 精確](fp-specify-floating-point-behavior.md)切換：

> cl /fp： 精確 source.cpp

這會指示編譯器使用 fp： 產生 source.cpp 檔案的程式碼時的精確語意。 Fp： 精確的模型也可根據函式的函式使用叫用[float_control 編譯器 pragma](#the-float-control-pragma)。

下 fp： 精確模式中，編譯器永遠不會執行任何擾亂浮點計算精確度的最佳化。 編譯器一律會在指派正確捨、 類型轉換和函式呼叫，以及中繼捨入不會一致地執行於相同的精確度 FPU 註冊。 預設會啟用安全的最佳化，例如的縮寫。 預設會停用例外狀況語意和 FPU 環境敏感度。

|fp： 精確語意|說明|
|-|-|
|捨入語意|在指派的明確捨入類型轉換和函式呼叫。 中繼運算式會評估在暫存器的有效位數。|
|代數轉換|嚴格遵循非關聯、 非分散浮點代數中，除非轉換保證在一律產生相同的結果。|
|縮寫|允許預設值。 如需詳細資訊，請參閱下一節[fp_contract pragma](#the-fp-contract-pragma)。|
|浮點數的評估順序|編譯器可能會重新排序浮點運算式的評估，前提是最終的結果，不會改變。|
|FPU 環境存取|預設為停用。 如需詳細資訊，請參閱下一節[fenv_access pragma](#the-fenv-access-pragma)。 假設的預設有效位數和捨入模式。|
|浮點例外狀況語意|預設為停用。 如需詳細資訊，請參閱 < [/fp： 除了](fp-specify-floating-point-behavior.md)。|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpprecise"></a>捨入下 fp 浮點運算式的語意： 精確

Fp： 精確的模型永遠執行最實際最高精確度，明確地只在特定時間點在運算式評估中捨入的中繼計算。 捨入為使用者指定有效位數一律會發生在四個位置: （a） 進行指派時，（b） typecast 執行時，（c） 時的浮點值的形式傳遞引數函式，並從傳回浮點值 （d）函式。 因為中繼計算一律會執行在暫存器的有效位數，中繼結果的精確度是平台相依 (有效位數一律會至少和指定的使用者為精確但有效位數)。

請考慮下列程式碼中的，指派運算式。 將在暫存器的有效位數，計算在右手邊的指派運算子 '=' 的運算式，並將其明確四捨五入到指派左手邊的型別。

```cpp
float a, b, c, d;
double x;
...
x = a*b + c*d;
```

計算方式為

```cpp
float a, b, c, d;
double x;
...
register tmp1 = a*b;
register tmp2 = c*d;
register tmp3 = tmp1+tmp2;
x = (double) tmp3;
```

若要明確地四捨五入中繼結果，導入 typecast。 例如，如果修改先前的程式碼加入明確類型轉換，中繼運算式 (c * d) 的 typecast 型別，會捨去。

```cpp
float a, b, c, d;
double x;
// . . .
x = a*b + (float)(c*d);
```

計算方式為

```cpp
float a, b, c, d;
double x;
// . . .
register tmp1 = a*b;
float tmp2 = c*d;
register tmp3 = tmp1+tmp2;
x = (double) tmp3;
```

此捨入方法的其中一個含義為一些看似對等的轉換沒有真正安裝相同的語意。 比方說，下列轉換會分割成兩個指派運算式的單一指派運算式。

```cpp
float a, b, c, d;
// . . .
a = b*(c+d);
```

不等於

```cpp
float a, b, c, d;
// . . .
a = c+d;
a = b*a;
```

同樣地：

```cpp
a = b*(c+d);
```

不等於

```cpp
a = b*(a=c+d);
```

這些編碼方式並沒有對等的語意，因為第二個編碼每一個導入了其他的指派運算，並因此其他的捨入點。

當函式傳回浮點值時，值會捨入至函式的類型。 當浮點數值做為參數傳遞至函式時，值會捨入至參數的型別。 例如: 

```cpp
float sumsqr(float a, float b)
{
   return a*a + b*b;
}
```

計算方式為

```cpp
float sumsqr(float a, float b)
{
    register tmp3 = a*a;
    register tmp4 = b*b;
    register tmp5 = tmp3+tmp4;
    return (float) tmp5;
}
```

同樣地：

```cpp
float w, x, y, z;
double c;
...
c = symsqr(w*x+y, z);
```

計算方式為

```cpp
float x, y, z;
double c;
...
register tmp1 = w*x;
register tmp2 = tmp1+y;
float tmp3 = tmp2;
c = symsqr( tmp3, z);
```

### <a name="architecture-specific-rounding-under-fpprecise"></a>架構特有的捨入下 fp： 精確

|處理器|捨入中繼運算式的有效位數|
|-|-|
|x86|中繼運算式計算的預設 53 個位元有效位數與延伸範圍提供的 16 位元的指數。 當這些 53:16 值會 「 溢出 」 至記憶體 （如有可能發生在函式呼叫期間） 時，擴充的指數範圍會縮小到 11 個位元。 也就是溢出的值會轉換成標準的雙精度格式與只有 11 位元的指數。<br/>使用者可能會切換至延伸的 64 位元精確度，來改變浮點控制字組使用捨入中繼`_controlfp`並啟用 FPU 環境存取 (請參閱 < [fenv_access pragma](#the-fenv-access-pragma))。 不過，當擴充的有效位數的暫存器值會溢出到記憶體中，中繼結果仍然會四捨五入為雙精度。<br/>這個特定的語意會有所變更。|
|amd64|在 amd64 FP 語意會稍有不同，從其他平台。 基於效能考量，中繼作業會計算最廣泛的精確度，而不是其中一個運算元，在可用的最大位數。  若要強制使用更多有效位數比運算元要計算的計算，使用者需要導入子運算式中的至少一個運算元的型別轉換作業。<br/>這個特定的語意會有所變更。|

### <a name="algebraic-transformations-under-fpprecise"></a>代數轉換下 fp： 精確

當 fp： 啟用精確模式時，編譯器將永遠不會執行代數轉換*除非最後的結果是可以證明相同*。 許多熟悉的代數規則的實際數字算術中不一定支援浮點算術。 例如，下列運算式是對等 Reals，但不是一定是浮點數。

|表單|描述|
|-|-|
|`(a+b)+c = a+(b+c)`|新增關聯規則|
|`(a*b)*c = a*(b*c)`|用於乘法的關聯規則|
|`a*(b+c) = a*b + b*c`|透過新增乘法分布|
|`(a+b)(a-b) = a*a-b*b`|代數分解|
|`a/b = a*(1/b)`|除數乘法反元素|
|`a*1.0 = a`|乘法單位元素|

此函式簡介範例所示`KahanSum`，編譯器可能會想要執行各種不同的代數轉換，以產生更快速的程式。 雖然最佳化依賴這類代數轉換幾乎永遠都不正確，但也有些情況下，它們是完全安全。 比方說，有時會需要取代除數*常數*值相乘的乘法反元素的常數：

```cpp
const double four = 4.0;
double a, b;
...

a = b/four;
```

可能會轉換成

```cpp
const double four = 4.0;
const double tmp0 = 1/4.0;
double a, b;
...
a = b*tmp0;
```

這是安全的轉換，因為最佳化工具可以判斷在編譯時期 x / 4.0 = = x*(1/4.0) 所有浮點值的 x，包括將無限大和 NaN。 藉由取代乘法的除法運算，編譯器可以儲存數個週期 — 尤其是在不直接實作分區，但需要編譯器產生的倒數近似值組合，並乘號加入 FPUs指示。 編譯器可能會執行這類最佳化下 fp： 精確取代乘法運算會產生精確時，才相同結果為除法運算。 編譯器也會執行 trivial 轉換下 fp: precise，前提是結果完全相同。 它們包括：

|表單|描述
|-|-|
|`(a+b) == (b+a)`|新增交換式規則|
|`(a*b) == (b*a)`|用於乘法交替的規則|
|`1.0*x*y == x*1.0*y == x*y*1.0 == x*y`|乘以 1.0|
|`x/1.0*y == x*y/1.0 == x*y`|除以 1.0|
|`2.0*x == x+x`|乘法 2.0|

### <a name="contractions-under-fpprecise"></a>Fp 下的縮寫： 精確

許多現代的浮點單位的主要架構功能是能夠執行乘法，後面接著新增做為單一作業，而且任何中繼的捨入錯誤。 比方說，Intel Itanium 架構會提供指示說明如何合併其中每個三元作業，(*b + c)，(* b + c) 和 (c a * b)，成單一的浮點指示 (fma、 fm 和 fnma 分別)。 這些單一指示速度比執行個別相乘，並新增指示，並且也更精確，因為沒有中繼進位的產品。 此最佳化可以大幅加快包含多項 multiply 交錯的函式，並將作業新增。 例如，請考慮下列演算法會計算兩個的 n 維向量內積。

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

可以執行這項計算一系列的乘號加入指示表單 p = p + x [i] * y [i]。

縮減最佳化可以會分別受到控管使用`fp_contract`編譯器 pragma。 根據預設，/fp： 精確的模型可讓的縮寫，因為它們改善精確度和速度。 在 /fp: precise，編譯器將永遠不會合約與明確的捨入運算式。
範例

```cpp
float a, b, c, d, e, t;
...
d = a*b + c;         // may be contracted
d += a*b;            // may be contracted
d = a*b + e*d;       // may be contracted into a mult followed by a mult-add
etc...

d = (float)a*b + c;  // won't be contracted because of explicit rounding

t = a*b;             // (this assignment rounds a*b to float)
d = t + c;           // won't be contracted because of rounding of a*b
```

### <a name="order-of-floating-point-expression-evaluation-under-fpprecise"></a>Fp 浮點運算式評估的順序： 精確

保留的浮點運算式的評估順序的最佳化永遠是安全，並因此會允許下 fp： 精確模式。 請考慮下列函式會計算兩個單精確度中的 n 維向量的內積。 下方的第一個程式碼區塊原始函式做為它可能會編碼為程式設計人員，由後面接著相同的函式之後的部分迴圈展開最佳化。

```cpp
//original function
float dotProduct( float x[], float y[], int n )
{
   float p=0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}

//after a partial loop-unrolling
float dotProduct( float x[], float y[], int n )
{
   int n4= n/4*4; // or n4=n&(~3);
   float p=0;
   int i;

   for (i=0; i<n4; i+=4)
   {
      p+=x[i]*y[i];
      p+=x[i+1]*y[i+1];
      p+=x[i+2]*y[i+2];
      p+=x[i+3]*y[i+3];
   }

   // last n%4 elements
   for (; i<n; i++)
      p+=x[i]*y[i];

   return p;
}
```

此最佳化的主要優點是，它會減少的條件式迴圈分支數高達 75%。 此外，藉由增加迴圈主體內的作業數目，編譯器現在可能會有更多的機會，以進一步最佳化。 比方說，可能可以執行一些 FPUs 乘號加入在 p + = x [i] * y [i] 時同時擷取 x [i + 1] 的值和 y [i + 1] 的下一個步驟中使用。 這種類型是最佳化的完全安全計算浮點數的因為它會保留作業的順序。

通常很有幫助，讓編譯器重新排列整個作業，以產生更快的程式碼。 請考慮下列程式碼：

```cpp
double a, b, c, d;
double x, y, z;
...
x = a*a*a + b*b*b + c*c*c;
...
y = a*a + b*b + c*c;
...
z = a + b + c;
```

C + + 語意規則指出程式應該產生的結果，如同第一次計算 x 則 y 和 z 最後。 假設編譯器有可用的只有四個浮點數暫存器。 如果強制編譯器來計算 x、 y 和 z 順序的情況下，它可能會選擇產生程式碼具有下列語意：

```cpp
double a, b, c, d;
double x, y, z;
register r0, r1, r2, r3;
...
// Compute x
r0 = a;         // r1 = a*a*a
r1 = r0*r0;
r1 = r1*r0;
r0 = b;         // r2 = b*b*b
r2 = r0*r0;
r2 = r2*r0;
r0 = c;         // r3 = c*c*c
r3 = r0*r0;
r3 = r3*r0;
r0 = r1 + r2;
r0 = r0 + r3;
x = r0;         // x = r1+r2+r3
// . . .
// Compute y
r0 = a;         // r1 = a*a
r1 = r0*r0;
r0 = b;         // r2 = b*b
r2 = r0*r0;
r0 = c;         // r3 = c*c
r3 = r0*r0;
r0 = r1 + r2;
r0 = r0 + r3;
y = r0;         // y = r1+r2+r3
// . . .
// Compute z
r1 = a;
r2 = b;
r3 = c;
r0 = r1 + r2;
r0 = r0 + r3;
z = r0;         // z = r1+r2+r3
```

有數個清楚地重複的作業是這種編碼方式。 如果編譯器完全遵循 c + + 語意規則時，這種排序，因為程式可能會存取 FPU 環境之間每個指派。 不過，fp 的預設設定： 精確允許編譯器最佳化如同程式不會存取環境，讓它可以重新排列這些運算式。 您就可以移除備援，藉由計算的三個值，以相反順序，如下：

```cpp
double a, b, c, d;
double x, y, z;
register r0, r1, r2, r3;
...
// Compute z
r1 = a;
r2 = b;
r3 = c;
r0 = r1+r2;
r0 = r0+r3;
z = r0;
...
// Compute y
r1 = r1*r1;
r2 = r2*r2;
r3 = r3*r3;
r0 = r1+r2;
r0 = r0+r3;
y = r0;
...
// Compute x
r0 = a;
r1 = r1*r0;
r0 = b;
r2 = r2*r0;
r0 = c;
r3 = r3*r0;
r0 = r1+r2;
r0 = r0+r3;
x = r0;
```

這種編碼方式是可清楚，讓縮減幾乎是 40 %fp 指令數目。 結果的 x、 y 和 z 都相同，但使用較少額外負荷計算。

下 fp: precise，編譯器可能會也*交錯式*通用子運算式，以產生更快的程式碼。 例如，程式碼以計算二次方程式的根目錄可能會撰寫，如下所示：

```cpp
double a, b, c, root0, root1;
...
root0 = (-b + sqrt(b*b-4*a*c))/(2*a);
root1 = (-b - sqrt(b*b-4*a*c))/(2*a);
```

雖然這些運算式差異只在單一作業，程式設計人員可能會撰寫這種方式，以確保每個根值，會計算最高的實際精確度。 下 /fp: precise，編譯器可以自由地交錯式 root0 和 root1 移除而不會遺失有效位數的通用子運算式的計算。 比方說，下列已移除數個多餘的步驟時產生完全相同的答案。

```cpp
double a, b, c, root0, root1;
...
register tmp0 = -b;
register tmp1 = sqrt(b*b-4*a*c);
register tmp2 = 2*a;
root0 = (tmp0+tmp1)/tmp2;
root1 = (tmp0-tmp1)/tmp2;
```

其他最佳化可能會嘗試將移特定獨立運算式的評估。 請考慮下列演算法包含迴圈主體中條件式分支。

```cpp
vector<double> a(n);
double d, s;
// . . .
for (int i=0; i<n; i++)
{
   if (abs(d)>1.0)
      s = s+a[i]/d;
   else
      s = s+a[i]*d;
}
```

編譯器可能會偵測到運算式的值 (abs(d) > 1) 是不變迴圈主體內。 這可讓編譯器 「 提"if 外部迴圈主體中，將上述程式碼轉換成下列陳述式：

```cpp
vector<double> a(n);
double d, s;
// . . .
if (abs(d)>1.0)
   for (int i=0; i<n; i++)
      s = s+a[i]/d;
else
   for (int i=0; i<n; i++)
      s = s+a[i]*d;
```

轉換之後，有不再條件式分支中的迴圈主體，因此大幅提升整體效能的迴圈。 這種類型的最佳化是完全安全因為運算式評估 (abs(d) > 1.0) 無關的其他運算式。

發生 FPU 環境存取或浮點例外狀況，因為它們會變更語意的流程，被 contraindicated 這些類型的最佳化。 這種最佳化才可用在 fp： 精確模式因為 FPU 環境存取和浮點例外狀況語意預設為停用。 函式會存取 FPU 環境可以明確地使用停用這種最佳化`fenv_access`編譯器 pragma。 同樣地，使用浮點例外狀況的函式應該使用`float_control(except ... )`編譯器的 pragma (或使用 **/fp： 除了**命令列參數)。

在 [摘要] fp： 精確模式可讓編譯器在的最終結果不會改變，重新排序浮點運算式的評估和結果不相依於 FPU 環境或浮點例外狀況。

### <a name="fpu-environment-access-under-fpprecise"></a>Fp FPU 環境存取權： 精確

當 fp： 精確模式已啟用，則編譯器會假設程式不會無法存取，或改變 FPU 環境。 如稍早所述，這項假設可讓編譯器重新排列或移動浮點數的作業，以改善效率下 fp： 精確。

有些程式可能會使用 alter 浮點捨入方向`_controlfp`函式。 比方說，有些程式計算上限和算術運算上較低的誤差界限，藉由執行相同的計算兩次，第一次時往負無限大方向捨入，然後同時朝向正無限大捨入。 由於 FPU 提供便利的方式，來控制四捨五入，程式設計人員可以選擇藉由改變 FPU 環境變更捨入模式。 下列程式碼會計算確切的錯誤繫結的浮點數的乘法改變 FPU 環境。

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -&infin;
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );    // round to +&infin;
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

下 fp： 精確，編譯器一律會假設預設的 FPU 環境，讓最佳化工具可以自由地忽略呼叫`_controlfp`並降低上述的指派，以 cUpper = cLower = * b; 這顯然會產生不正確的結果。 若要避免這種最佳化，請使用，FPU 環境存取啟用`fenv_access`編譯器 pragma。

其他程式可能會嘗試偵測特定浮點數的錯誤檢查 FPU 狀態字組。 例如，下列程式碼會檢查除以零和精確狀況

```cpp
double a, b, c, r;
float x;
// . . .
_clearfp();
r = (a*b + sqrt(b*b-4*a*c))/(2*a);
if (_statusfp() & _SW_ZERODIVIDE)
   handle divide by zero as a special case
_clearfp();
x = r;
if (_statusfp() & _SW_INEXACT)
   handle inexact error as a special case
etc...
```

在 /fp: precise，最佳化重新排序運算式評估可能會變更某些錯誤就會發生的點。 存取狀態字組的程式應該使用啟用 FPU 環境存取`fenv_access`編譯器 pragma。

如需詳細資訊，請參閱下一節[fenv_access pragma](#the-fenv-access-pragma)。

### <a name="floating-point-exception-semantics-under-fpprecise"></a>Fp 下的浮點例外狀況語意： 精確

預設情況下，浮點例外狀況語意會停用下 fp： 精確。 大部分的 c + + 程式設計人員想要處理浮點數的例外狀況，而不使用系統或 c + + 例外狀況。 此外，如稍早所述，停用浮點例外狀況語意可讓編譯器更大的彈性最佳化浮點運算時。 使用任何一種 **/fp： 除了**切換或`float_control`使用 fp 時啟用浮點例外狀況語意的 pragma： 精確的模型。

如需詳細資訊，請參閱下一節[啟用浮點例外狀況語意](#enabling-floating-point-exception-semantics)。

## <a name="the-fpfast-mode-for-floating-point-semantics"></a>浮點語意 /fp: fast 模式

啟用 /fp: fast 模式時，編譯器會放寬規則該 fp： 精確的使用最佳化浮點運算時。 此模式會讓編譯器將進一步最佳化浮點程式碼的速度，但代價是浮點數的精確度和正確性。 請勿依賴高度精確的浮點運算的程式可能會遇到顯著的速度改進啟用 /fp: fast 模式。

/Fp: fast 浮點模式會使用啟用[/fp: fast](fp-specify-floating-point-behavior.md) ，如下所示的命令列編譯器參數：

> cl /fp: fast source.cpp

此範例會指示編譯器產生 source.cpp 檔案的程式碼時，使用 /fp: fast 語意。 /Fp: fast 模型也可叫用函式的函式為基礎，使用`float_control`編譯器 pragma。

如需詳細資訊，請參閱下一節[float_control pragma](#the-float-control-pragma)。

在 /fp: fast 模式下，編譯器可能會執行 alter 浮點計算精確度的最佳化。 編譯器可能不在指派正確捨、 類型轉換或函式呼叫，以及中繼捨入不一定會執行。 浮點特定的最佳化作業，例如的縮寫，一定會啟用。 浮點例外狀況語意和 FPU 環境敏感度是已停用而且無法使用。

|/fp: fast 語意|說明
|-|-|
|捨入語意|在指派的明確捨入類型轉換和函式呼叫可能會被忽略。<br/>在早於註冊根據效能需求的有效位數，可能會捨入中繼運算式。|
|代數轉換|編譯器可能會轉換運算式，根據實際數字關聯、 分散代數;這些轉換不是保證是正確或正確。|
|縮寫|一律啟用;無法停用 pragma `fp_contract`|
|浮點數的評估順序|編譯器可能會重新排序浮點運算式，評估，即使這類變更可能會改變最終的結果。|
|FPU 環境存取|已停用。 無法使用|
|浮點例外狀況語意|已停用。 無法使用|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpfast"></a>捨入下 /fp: fast 的浮點運算式的語意

不同於 fp： 精確的模型，/fp: fast 模型就會執行中繼的計算，在最方便的有效位數。 在指派，捨入的類型轉換和函式呼叫可能不一定會發生。 比方說，第一個函式的下列導入三個單精確度變數 (`C`，`Y`和`T`)。 編譯器可能會選擇低落這些變數時，作用中的型別提升`C`，`Y`和`T`以雙精確度。

原始的函式：

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0, C=0, Y, T;
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = T;
   }
   return sum;
}
```

變數的機率：

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0;
   double C=0, Y, T; // now held in-register
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = (float) T;
   }
   return sum;
}
```

在此範例中，/fp: fast 具有 subverted 原始函式的目的。 最終的最佳化結果，該變數中保存`sum`，可能會相當： 從正確的結果。

在 /fp: fast，編譯器通常會嘗試維護至少由原始程式碼所指定的精確度。 不過，在某些情況下，編譯器可能會選擇執行中繼運算式*降低有效位數*比在原始程式碼中所指定。 比方說，第一次下方的程式碼區塊會呼叫平方根函式的雙精確度版本。 在某些情況下，例如時的結果和運算元的函式會明確地轉換成單精確度，/fp: fast 下，編譯器可以選擇為雙精度的呼叫取代`sqrt`單精確度呼叫`sqrtf`函式。 因為確定傳入的值轉型`sqrt`和推出的值會捨入到單精確度，這只會變更的捨入的位置。 如果進入 sqrt 的值是雙精度值，而編譯器執行此轉換，多達一半的精確度位元可能的錯誤。

原始的函式

```cpp
double sqrt(double);
// . . .
double a, b, c;
float f1, f2;
// . . .
float length = (float)sqrt((float)(a*a + b*b + c*c));
float sum = (float) ((double)f1 + (double)f2);
```

最佳化函式

```cpp
float sqrtf(float)...
// . . .
double a, b, c;
float f1, f2;
// . . .
double tmp0 = a*a + b*b + c*c;
float tmp1 = tmp0;    // round of parameter value
float length = sqrtf(tmp1); // rounded sqrt result
float sum = f1 + f2;
```

雖然較不精確，此最佳化可能會特別有幫助以提供單一有效位數，內建函式版本，例如的處理器為目標時`sqrt`。 只要精確時，編譯器將使用這種最佳化是平台和內容相依。

此外，還有中繼計算，這可能會執行任何可供編譯器的有效位數層級的有效位數不保證的一致性。 雖然編譯器會嘗試維持最少的程式碼所指定的有效位數層級，/fp: fast 會允許向下轉型的中繼計算最佳化工具以產生更快或較小的機器碼。 比方說，編譯器可能會進一步要捨入為單精確度中繼的乘法運算的一些最佳化從上述程式碼。

```cpp
float sqrtf(float)...
// . . .
double a, b, c;
float f1, f2;
// . . .
float tmp0 = a*a;     // round intermediate a*a to single-precision
float tmp1 = b*b;     // round intermediate b*b to single-precision
double tmp2 = c*c;    // do NOT round intermediate c*c to single-precision
float tmp3 = tmp0 + tmp1 + tmp2;
float length = sqrtf(tmp3);
float sum = f1 + f2;
```

從使用較低精確度浮點單位，例如 SSE2，來執行某些中繼計算，可能會造成這種額外的捨入。 因此，/fp: fast 四捨五入的精確度是平台相依;適用於一個處理器編譯的程式碼可能不一定適用於另一個處理器。 它是保留給使用者，以判斷是否速度效益遠大於任何精確度的問題。

/Fp: fast 最佳化特別有問題的特定函式時，浮點模式可以從本機切換到 fp： 設定使用的精確`float_control`編譯器 pragma。


### <a name="algebraic-transformations-under-fpfast"></a>在 /fp: fast 的代數轉換

/Fp: fast 模式可讓編譯器執行特定項目，不安全的代數轉換，以浮動點運算式。 例如，下列不安全的最佳化可能會採用下 /fp: fast。

||||
|-|-|-|
|原始的程式碼|步驟 1|步驟 2
|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = y – a – b;`<br/><br/>`c = x – z;`<br/><br/>`c = x * z;`<br/><br/>`c = x - z;`<br/><br/>`c = x + z;`<br/><br/>`c = z-x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x – 0;`<br/><br/>`c = x * 0;`<br/><br/>`c = x - 0;`<br/><br/>`c = x + 0;`<br/><br/>`c = 0 - x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x;`<br/><br/>`c = 0;`<br/><br/>`c = x;`<br/><br/>`c = x;`<br/><br/>`c = -x;`|

在步驟 1 中，編譯器會觀察，`z = y – a – b`會一律等於零。 雖然就技術上而言是無效的觀察，它允許在 /fp: fast。 然後，編譯器會傳播變數 z，每個後續使用常數的值為零。 在步驟 2 中，進一步的編譯器最佳化，觀察`x - 0 == x`，`x * 0 == 0`等等。同樣地，即使這些觀察不完全有效，但它們所許可的 /fp: fast。 最佳化的程式碼現在更快，但也可能是較不精確或甚至是不正確。

啟用 /fp: fast 模式時，您可能必須使用任何下列 （不安全） 的代數規則，最佳化工具：

|||
|-|-|
|表單|描述|
|`(a + b) + c = a + (b + c)`|新增關聯規則|
|`(a * b) * c = a * (b * c)`|用於乘法的關聯規則|
|`a * (b + c) = a * b + b * c`|透過新增乘法分布|
|`(a + b)(a - b) = a * a - b * b`|代數分解|
|`a / b = a * (1 / b)`|除數乘法反元素|
|`a * 1.0 = a, a / 1.0 = a`|乘法單位元素|
|`a ± 0.0 = a, 0.0 - a = -a`|加法單位|
|`a / a = 1.0, a - a = 0.0`|取消|

/Fp: fast 最佳化特別有問題的特定函式時，浮點模式可以從本機切換到 fp： 設定使用的精確`float_control`編譯器 pragma。

### <a name="order-of-floating-point-expression-evaluation-under-fpfast"></a>/Fp: fast 浮點運算式評估的順序

不同於 /fp: precise，/fp: fast，可讓編譯器重新排序浮點運算，以產生更快的程式碼。 因此，在 /fp: fast 某些最佳化可能不會保留運算式的預期的順序。 比方說，假設有下列函式，會計算兩個的 n 維向量的內積。

```cpp
float dotProduct( float x[], float y[],
                  int n )
{
   float p=0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

在底下，/fp: fast，最佳化工具可能會執行的純量減少`dotProduct`函式有效地轉換函式，如下所示：

```cpp
float dotProduct( float x[], float y[],int n )
{
    int n4= n/4*4; // or n4=n&(~3);
    float p=0, p2=0, p3=0, p4=0;
    int i;

    for (i=0; i<n4; i+=4)
    {
        p+=x[i]*y[i];
        p2+=x[i+1]*y[i+1];
        p3+=x[i+2]*y[i+2];
        p4+=x[i+3]*y[i+3];
    }
    p+=p2+p3+p4;

    // last n%4 elements
    for (; i<n; i++)
    p+=x[i]*y[i];

    return p;
}
```

在函式的最佳化版本四個不同的產品就是同時採用，並再加在一起。 此最佳化可加快計算`dotProduct`由更的四個根據目標處理器，但最終結果的因素可能會因此不正確，並使它。 如果這種最佳化是特別有問題的單一函式 」 或 「 轉譯單位，浮點模式可以從本機切換到 fp： 設定使用的精確`float_control`編譯器 pragma。

## <a name="the-fpstrict-mode-for-floating-point-semantics"></a>/Fp: strict 模式浮點語意

當 /fp: strict 模式下，編譯器遵守相同的所有規則的 fp： 精確的使用最佳化浮點運算時。 此模式也會啟用浮點例外狀況語意和 FPU 環境的敏感度，並停用某些最佳化功能，例如縮寫。 它是作業的最嚴格模式。

/Fp: strict 浮點數的模式會使用啟用[/fp: strict](fp-specify-floating-point-behavior.md) ，如下所示的命令列編譯器參數：

> cl /fp: strict source.cpp

此範例會指示編譯器使用 /fp: strict 產生 source.cpp 檔案的程式碼時的語意。 /Fp: strict 模型也可叫用函式的函式為基礎，使用`float_control`編譯器 pragma。

如需詳細資訊，請參閱下一節[float_control pragma](#the-float-control-pragma)。

在 /fp: strict 模式中，編譯器永遠不會執行任何擾亂浮點計算精確度的最佳化。 編譯器一律會在指派正確捨、 類型轉換和函式呼叫，以及中繼捨入不會一致地執行於相同的精確度 FPU 註冊。 預設會啟用浮點例外狀況語意和 FPU 環境敏感度。 已停用某些最佳化功能的縮寫，例如，因為編譯器無法保證在每個案例的正確性。

|/fp: strict 語意|說明|
|-|-|
|捨入語意|在指派的明確捨入類型轉換和函式呼叫<br/>中繼運算式會評估在暫存器的有效位數。<br/>相同 fp： 精確|
|代數轉換|嚴格遵循非關聯、 非分散浮點代數中，除非轉換保證在一律產生相同的結果。<br/>相同 fp： 精確|
|縮寫|一律停用|
|浮點數的評估順序|編譯器不會重新排列浮點運算式的評估|
|FPU 環境存取|永遠啟用。|
|浮點例外狀況語意|預設為啟用。|

### <a name="floating-point-exception-semantics-under-fpstrict"></a>Fp 下的浮點例外狀況語意： strict

根據預設，在 fp 啟用浮點例外狀況語意： strict 模型。 若要停用這些語意，請使用 **/fp： 除了-** 切換，或引進`float_control(except, off)`pragma。

如需詳細資訊，請參閱章節[啟用浮點例外狀況語意](#enabling-floating-point-exception-semantics)並[float_control Pragma](#the-float-control-pragma)。

## <a name="the-fenvaccess-pragma"></a>Fenv_access pragma

使用方式：

```cpp
#pragma fenv_access( [ on  | off ] )
```

[Fenv_access](../../preprocessor/fenv-access.md) pragma 可讓編譯器將 FPU 旗標測試和 FPU 模式變更可能會破壞的某些最佳化功能。 當狀態`fenv_access`停用，則編譯器會假設預設 FPU 模式才有效，並不會測試 FPU 旗標。 根據預設，環境存取已停用 fp： 精確模式，但它可能明確啟用使用這個 pragma。 在 /fp: strict，`fenv_access`永遠啟用，而且無法停用。 在 /fp: fast，`fenv_access`一律停用，而且無法啟用。

Fp 中所述： 精確的區段中，某些程式設計人員可能會改變浮點捨入方向使用`_controlfp`函式。 比方說，若要計算上限和下限誤差界限上的算術運算，有些程式執行相同計算兩次，第一次時往負無限大捨入，然後同時朝向正無限大捨入。 由於 FPU 提供便利的方式，來控制四捨五入，程式設計人員可以選擇藉由改變 FPU 環境變更捨入模式。 下列程式碼會計算確切的錯誤繫結的浮點數的乘法改變 FPU 環境。

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -infinity
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );       // round to +infinity
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

停用時， `fenv_access` pragma 可讓編譯器来假設預設 FPU 環境; 因此，最佳化工具是可忽略的呼叫`_controlfp`，並降低上述的指派，以`cUpper = cLower = a*b`。 啟用時，不過，`fenv_access`可避免這種最佳化。

程式也可以查看 FPU 狀態字組，來偵測特定浮點數的錯誤。 例如，下列程式碼會檢查除以零和精確狀況

```cpp
double a, b, c, r;
float x;
// . . .
_clearfp();
r = (a*b + sqrt(b*b-4*a*c))/(2*a);
if (_statusfp() & _SW_ZERODIVIDE)
   handle divide by zero as a special case
_clearfp();
x = (a*b + sqrt(b*b-4*a*c))/(2*a);
if (_statusfp() & _SW_INEXACT)
   handle inexact error as a special case
etc...
```

當`fenv_access`是停用，編譯器可能會重新排列的執行順序的浮點運算式，因此可能破壞 FPU 狀態檢查。 啟用`fenv_access`可避免這種最佳化。

## <a name="the-fpcontract-pragma"></a>Fp_contract pragma

使用方式：

```cpp
#pragma fp_contract( [ on | off ] )
```

Fp 中所述： 精確區段中，縮減是許多現代的浮點單位的基本架構功能。 縮寫提供執行乘法，後面接著新增做為單一作業，而且任何中繼的捨入錯誤的能力。 這些單一指示速度比執行個別相乘，並新增指示，並且也更精確，因為沒有中繼進位的產品。 合約的作業可以計算的值`(a*b+c)`如同這兩項作業一般計算至無限精確度，且就會四捨五入至最接近的浮點數。 此最佳化可以大幅加快包含多項 multiply 交錯的函式，並將作業新增。 例如，請考慮下列演算法會計算兩個的 n 維向量內積。

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

可以執行這項計算一系列的乘號加入表單的指示`p = p + x[i]*y[i]`。

[Fp_contract](../../preprocessor/fp-contract.md) pragma 可讓您指定是否可以縮減浮點運算式。 根據預設，/fp： 精確模式可讓的縮寫，因為它們改善精確度和速度。 /Fp: fast 模式一定會啟用的縮寫。 不過，因為縮寫可破壞明確偵測錯誤狀況， `fp_contract` pragma 一律停用在 /fp: strict 模式。 可能的運算式的範例簽約時`fp_contract`pragma 會啟用：

```cpp
float a, b, c, d, e, t;
...
d = a*b + c;         // may be contracted
d += a*b;            // may be contracted
d = a*b + e*d;       // may be contracted into a mult followed by a mult-add etc...

d = (float)a*b + c;  // won't be contracted because of explicit rounding

t = a*b;             // (this assignment rounds a*b to float)
d = t + c;           // won't be contracted because of rounding of a*b
```

## <a name="the-floatcontrol-pragma"></a>Float_control pragma

**/Fp： 精確**， **/fp: fast**， **/fp: strict**並 **/fp： 除了**參數控制浮點語意上由檔案的檔案基準。 [Float_control](../../preprocessor/float-control.md) pragma 提供這類函式的函式為基礎的控制項。

使用方式：

```cpp
#pragma float_control(push)
#pragma float_control(pop)
#pragma float_control( precise, on | off [, push] )
#pragma float_control( except, on | off [, push] )
```

Pragma`float_control(push)`和`float_control(pop)`分別 push 和 pop 的浮點數的模式和至堆疊的例外狀況 選項的目前狀態。 請注意，狀態`fenv_access`並`fp_contract`pragma 不會受到`pragma float_control(push/pop)`。

呼叫 pragma`float_control(precise, on)`可讓和`float_control(precise, off)`將會停用精確模式語意。 同樣地，pragma`float_control(except, on)`可讓和`float_control(except, off)`將會停用例外狀況語意。 只有精確語意也會啟用時，才可以啟用例外狀況語意。 當選擇性`push`引數已存在，狀態`float_control`變更語意之前推入選項。

### <a name="setting-the-floating-point-semantic-mode-on-a-function-by-function-basis"></a>設定函式的函式為基礎的浮點語意模式

命令列參數實際上會設定四個不同的浮點 pragma 的速記。 若要明確地選擇特定浮點語意模式函式的函式為基礎，選取每個下表中所述的四個浮點數選項 pragma:

||||||
|-|-|-|-|-|
||float_control(precise)|float_control(except)|fp_contract|fenv_access|
|/fp: strict|於|於|關閉|於|
|/fp: strict /fp： 除了-|於|關閉|關閉|於|
|/fp： 精確|於|關閉|於|關閉|
|/fp: precise /fp： 除外|於|於|於|關閉|
|/fp: fast|關閉|關閉|於|關閉|

例如，下列明確啟用 /fp: fast 語意。

```cpp
#pragma float_control( except, off )   // disable exception semantics
#pragma float_control( precise, off )  // disable precise semantics
#pragma fp_contract(on)                // enable contractions
#pragma fenv_access(off)               // disable fpu environment sensitivity
```

> [!Note]
> 例外狀況語意必須關閉之前關閉"precise"語意。

## <a name="enabling-floating-point-exception-semantics"></a>啟用浮點例外狀況語意

特定例外狀況之浮點數的條件，例如除以零，可能會導致 FPU 發出信號的硬體例外狀況。 預設會停用浮點例外狀況。 藉由修改 FPU 控制字組，以啟用浮點例外狀況`_controlfp`函式。 例如，下列程式碼可讓零除以浮點例外狀況：

```cpp
_clearfp(); // always call _clearfp before
            // enabling/unmasking a FPU exception
_controlfp( _EM_ZERODIVIDE, _MCW_EM );
```

啟用時的除以零例外狀況，任何分母等於零的除法運算會收到信號的 FPU 例外狀況。

若要還原為預設模式的 FPU 控制字組，請呼叫`_controlfp(_CW_DEFAULT, ~0)`。

啟用與浮點例外狀況語意 **/fp： 除了**旗標不相同啟用浮點例外狀況。 啟用浮點例外狀況語意時，編譯器必須負責任何浮點運算可能會擲回例外狀況的可能性。 由於 FPU 是不同的處理器單元，可以與其他單位上的指示同時執行 FPU 上執行的指示。

啟用浮點例外狀況時，FPU 將暫止的有問題的指示執行，並再表示 splittunneling FPU 狀態字組的 例外狀況。 當 CPU 達到下一個浮點指令時，它首先會檢查任何暫止的 FPU 例外狀況。 如果沒有暫止例外狀況，處理器就會對它呼叫作業系統所提供的例外狀況處理常式。 這表示，當浮點運算發生例外狀況時，對應的例外狀況將偵測不到下一個浮點作業執行之前。 例如，下列程式碼所截獲除以零例外狀況：

```cpp
double a, b, c;
// . . .
// ...unmasking of FPU exceptions omitted...
__try
{
   b/c; // assume c==0.0
   printf("This line shouldn't be reached when c==0.0\n");
   c = 2.0*b;
}
__except( EXCEPTION_EXECUTE_HANDLER )
{
   printf("SEH Exception Detected\n");
}
// . . .
```

如果在運算式中就會發生除以零的狀況 = b/c FPU 將不會設陷/引發的例外狀況，直到下一步 的浮點運算中的運算式 2.0 * b。 這會導致下列輸出：

```Output
This line shouldn't be reached when c==0.0
SEH Exception Detected
```

對應至輸出的第一行 printf 應該尚未達到;它已達到因為浮點運算式 b/c 所造成的例外狀況未引發執行達到 2.0 * b。 若要引發的例外狀況之後執行 b/c，編譯器必須導入的"wait"指示：

```cpp
// . . .
   __try
   {
      b/c; // assume this expression will cause a "divide-by-zero" exception
      __asm fwait;
      printf("This line shouldn't be reached when c==0.0\n");
      c = 2.0*b;
   }
// . . .
```

這個 「 等候 」 的指示會強制處理器同步處理狀態為 FPU 及處理任何擱置中的例外狀況。 編譯器只會產生這些 「 等候 」 指示時啟用浮點語意。 停用這些語意，因為根據預設，程式可能會遇到類似上述的同步性錯誤使用浮點例外狀況時。

當啟用浮點語意時，編譯器並不只會產生 「 等候 」 指示時，它也會防止編譯器錯誤地最佳化浮點程式碼有可能的例外狀況。 這包括任何 alter 例外狀況擲回點的轉換。 這些因素，因為啟用浮點語意可能會大幅減少產生的機器程式碼造成應用程式的效能降低的效率。

Fp 下預設會啟用浮點例外狀況語意： strict 模式。 若要啟用這些語意中 fp： 精確模式中，新增 **/fp： 除了**切換到命令列編譯器。 浮點例外狀況語意亦可啟用和停用根據函式的函式使用`float_control`pragma。

### <a name="floating-point-exceptions-as-c-exceptions"></a>為 c + + 例外狀況的浮點例外狀況

與所有的硬體例外狀況，浮點例外狀況並本質上會造成 c + + 例外狀況，但改為觸發程序的結構化例外狀況。 若要以 c + + 例外狀況對應結構化的浮點例外狀況，使用者可能會引發自訂的 SEH 例外狀況轉譯器。 首先，導入對應至每個浮點例外狀況的 c + + 例外狀況：

```cpp
class float_exception : public std::exception {};

class fe_denormal_operand : public float_exception {};
class fe_divide_by_zero : public float_exception {};
class fe_inexact_result : public float_exception {};
class fe_invalid_operation : public float_exception {};
class fe_overflow : public float_exception {};
class fe_stack_check : public float_exception {};
class fe_underflow : public float_exception {};
```

然後，導入轉譯函式，將會偵測浮點數的 SEH 例外狀況，並擲回對應的 c + + 例外狀況。 若要使用此函式，設定目前處理序執行緒使用結構化例外狀況處理常式 translator [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)函式，從執行階段程式庫。

```cpp
void se_fe_trans_func( unsigned int u, EXCEPTION_POINTERS* pExp )
{
    switch (u)
    {
    case STATUS_FLOAT_DENORMAL_OPERAND:   throw fe_denormal_operand();
    case STATUS_FLOAT_DIVIDE_BY_ZERO:     throw fe_divide_by_zero();
   etc...
    };
}
// . . .
_set_se_translator(se_fe_trans_func);
```

此對應初始化之後，就好像它們是 c + + 例外狀況行為的浮點例外狀況。 例如: 

```cpp
try
{
   // floating-point code that might throw divide-by-zero
   // or other floating-point exception
}
catch(fe_divide_by_zero)
{
    cout << "fe_divide_by_zero exception detected" << endl;
}
catch(float_exception)
{
    cout << "float_exception exception detected" << endl;
}
```

## <a name="references"></a>參考

[每個電腦科學家應該了解浮點算術](http://pages.cs.wisc.edu/~david/courses/cs552/S12/handouts/goldberg-floating-point.pdf)由 David 錢。

## <a name="see-also"></a>另請參閱

[最佳化程式碼](optimizing-your-code.md)<br/>
