---
title: Microsoft Visual c + + 浮點最佳化 |Microsoft 文件
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 35c9263fa6252469124eefb0dfd575ef5bd2ac34
ms.sourcegitcommit: 5e932a0e110e80bc241e5f69e3a1a7504bfab1f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2018
ms.locfileid: "34422729"
---
# <a name="microsoft-visual-c-floating-point-optimization"></a>Microsoft Visual c + + 浮點最佳化

取得控制代碼上使用管理浮點語意的方法，Microsoft c + + 編譯器的浮點程式碼的最佳化。 建立快速的程式，同時確保在浮點程式碼會執行唯一安全的最佳化。

## <a name="optimization-of-floating-point-code-in-c"></a>C + + 中的浮點程式碼的最佳化

最佳化的 c + + 編譯器不只會將原始程式碼轉譯成機器碼，安排機器中的指示以提升效率及/或減少大小的方式。 不幸的是，不套用至計算浮點數時，一定是安全多的常見最佳化。 良好的範例可以看到與下列總和演算法，David 錢、 」 功能每次電腦科學家應該知道有關浮點運算 」，從*運算調查*、 第 1991 年 3 月 pg。 203:

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

此函式會將 n **float**陣列向量中的值`A`。 迴圈主體中，演算法會計算總和的下一個步驟來套用 「 更正 」 值。 這個方法可大幅減少相較於簡單的總和，同時保留 o （n） 的時間複雜性累計捨入錯誤。

貝氏 c + + 編譯器可能會假設浮點算術遵循相同的代數規則實數算術。 這類編譯器可能會接著錯誤地結束，

> C = T 總和-Y = = > （總和 + Y） 總和-Y = = > 0;

也就是說，C 的認知的值一律是常數零。 如果此常數值，然後會傳播到後續的運算式，在迴圈主體會縮短為簡單的總和。 更明確地說，

> Y = [i]-C = = > Y = [i]<br/>T = 總和 + Y = = > T = 總和 + [i]<br/>sum = T = = > 總計 = 總計 + [i]

因此，給貝氏編譯器，邏輯轉換`KahanSum`函式會：

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0; // C, Y & T are now unused
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

雖然已轉換的演算法是更快、*根本不是程式設計人員設計用意的精確表示*。 完全，已經移除了精心製作的錯誤修正，而且我們保有簡單且直接的總和演算法，其所有相關聯的錯誤。

當然，複雜的 c + + 編譯器就會知道此代數規則的真實算術通常不適用於浮點算術。 不過，更複雜的 c + + 編譯器可能仍然不正確地解譯程式設計人員的意圖。

請考慮常見的最佳化嘗試盡量值保存在暫存器中，盡可能 （稱為 「 註冊 （enregistering） 」 值）。 在`KahanSum`範例中，此最佳化可能會試著低落變數`C`，`Y`和`T`因為他們只在迴圈主體內的使用。 如果 52bits (double) 而不是 23bits （單一） 登錄的有效位數，此最佳化有效型別會提升`C`，`Y`和`T`輸入**double**。 如果總和變數同樣不是機率，它仍會以單精確度編碼。 這會將轉換的語意`KahanSum`下

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

雖然`Y`，`T`和`C`會立即計算精確度越高，在這個新的編碼可能會產生較不精確的結果中的值而定`A[]`。 因此即使看似無害的最佳化可能會有負面結果。

這類的最佳化問題並不限於使用 「 複雜 」 的浮點程式碼。 不正確地最佳化時，甚至是簡單的浮點演算法可能會失敗。 請考慮簡單且直接加總的演算法：

```cpp
float Sum( const float A[], int n )
{
   float sum=0;
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

某些浮點數的單位包括能夠同時執行多個作業，因為編譯器可能會選擇參與的純量減少最佳化。 此最佳化實際上會將上述簡單的 Sum 函數轉換成下列：

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

此函式現在會維護四個不同的框架，可以同時處理每個步驟。 雖然最佳化的函式現在是更快，最佳的結果可能會與非最佳化的結果相當不同。 在進行這項變更，編譯器會假設關聯浮點加法。也就是說，這些兩個運算式相等： `(a + b) + c == a + (b + c)`。 不過，關聯性不一定包含為浮點數值，則為 true。 而不是計算總和為：

```cpp
sum = A[0]+A[1]+A[2]+...+A[n-1];
```

已轉換的函式現在會計算與結果

```cpp
sum = (A[0]+A[4]+A[8]+...)
    + (A[1]+A[5]+A[9]+...)
    + (A[2]+A[6]+A[10]+...)
    + (A[3]+A[7]+A[11]+...);
```

中的某些值`A[]`，此不同排序加法作業可能會產生非預期的結果。 若要進一步讓事情更複雜，某些程式設計人員可能會選擇預期會發生這種最佳化，並適當地修正它們。 程式可以在此情況下，建構陣列`A`不同的順序，以便最佳化的總和會產生預期的結果。 此外，在許多情況下可能是 「 關閉夠 」 精確度的最佳化結果。 最佳化優點令人信服速度時，這是特別有用。 視訊遊戲，例如，需要進行更速度越好，但通常不需要高度精確的計算浮點數。 編譯器決策者因此必須提供用來控制的速度和精確性通常不同目標的程式設計人員的機制。

某些編譯器提供個別的交換器，每種類型的最佳化，以解決速度和精確性之間的權衡取捨。 這可讓開發人員若要停用造成變更他們的特定應用程式的浮點精確度的最佳化。 雖然這個解決方案可以提供較高程度的控制能力編譯器，它導入了幾個額外的問題：

- 通常會很清楚的切換成啟用或停用。
- 停用任何單一最佳化可能會影響效能的非浮點程式碼。
- 每個額外的參數會產生許多新的交換器組合。快速地組合的數目會變得不便。

因此每個最佳化提供不同的參數可能看起來很吸引人，而使用這類編譯器可以麻煩且不可靠。

許多 c + + 編譯器提供*一致性*浮點模型，(透過 **/Op**或 **/fltconsistency**切換) 可讓開發人員建立程式相容具有嚴格浮點語意。 時，此模型可防止編譯器在計算浮點數使用大部分的最佳化，同時允許這些最佳化的非浮點程式碼。 一致性模型，不過，有暗色調側邊。 為了在不同 FPU 架構的幾乎所有實作傳回可預測的結果 **/Op**捨入中繼運算式，以使用者指定的有效位數; 例如，下列運算式為例：

```cpp
float a, b, c, d, e;
// . . .
a = b * c + d * e;
```

為了產生一致且可重複的結果，在 **/Op**，此運算式取得評估為它實作了，如下所示：

```cpp
float x = b  *c;
float y = d * e;
a = x + y;
```

最終的結果現在會受到單精確度捨入錯誤*每個步驟中評估運算式*。 雖然此解譯絕對不會中斷任何 c + + 語意規則，幾乎永遠不會是最佳的方式來評估浮點運算式。 它是計算的中繼結果方面以原狀實際的精確度最高通常更為理想。 比方說，它會是較好的方式計算運算式`a = b * c + d * e`中較高的有效位數為中

```cpp
double x = b * c;
double y = d * e;
double z = x + y;
a = (float)z;
```

或最好使用

```cpp
long double x = b * c;
long double y = d * e
long double z = x + y;
a = (float)z;
```

在計算中較高精確度的中繼結果，最終結果是明顯更精確的。 諷刺，採用一致性模型，錯誤的可能性會增加時，使用者嘗試停用不安全的最佳化，以減少錯誤。 因此一致性模型會嚴重降低效率時同時提供提高精確度不保證一定。 嚴重的數值程式設計人員而言，這似乎不是很好的權衡取捨類似，而且是，此模型未通常也收到的主要原因。

從版本 8.0 (C++® 2005)，Microsoft c + + 編譯器會提供更佳的替代方式。 它可讓程式設計人員可以選擇三種一般的浮點模式之一： fp： 精確： fast 且 /fp: strict。

- 下 fp: precise，只有安全會執行最佳化浮點程式碼上，而且不同於 **/Op**，中繼的計算以一致的方式執行位於最高的實際精確度。
- : fast 模式會放寬以更積極的最佳化，但會犧牲精確度浮點數的規則。
- /fp: strict 模式提供的 fp 所有一般正確性： 精確時啟用 fp 例外狀況語意，並避免出現 FPU 環境變更 （例如變更暫存器的精確度，捨入方向等） 不合法的轉換。

浮點例外狀況語意可以獨立控制透過命令列參數或編譯器的 pragma。根據預設，浮點例外狀況語意會停用下 fp： 精確且已啟用下 fp: strict。 編譯器也提供控制權 FPU 環境機密性和用特定浮點數的特定最佳化，例如的縮寫。 這個簡單的模型可讓開發人員更多的控制而不需要太多編譯器參數負擔或非預期的副作用的潛在的浮點程式碼的編譯。

## <a name="the-fpprecise-mode-for-floating-point-semantics"></a>Fp： 浮點語意的精確模式

預設的浮點語意模式是 fp： 精確。 選取此模式時，編譯器嚴格遵守一組安全性規則時最佳化浮點運算。 這些規則可讓編譯器產生有效率機器碼維持計算浮點數的精確度。 為了方便快速的實際執行程式，fp： 精確的模型停用浮點例外狀況語意 （雖然它們可以明確地啟用）。 Microsoft 已選取 fp： 精確做為預設的浮點模式因為它會建立快速且正確的程式。

若要明確地要求 fp： 使用命令列編譯器使用的精確模式[/fp： 精確](fp-specify-floating-point-behavior.md)切換：

> cl /fp： 精確 source.cpp

這會指示編譯器使用 fp： 產生 source.cpp 檔的程式碼時的精確語意。 Fp： 精確的模型可以也叫用函式的函式使用[float_control 編譯器 pragma](#the-float-control-pragma)。

下 fp： 精確模式中，編譯器永遠不會執行任何擾亂浮點計算精確度的最佳化。 編譯器一律會在指派正確無條件、 類型轉換和函式呼叫，且中繼捨入會一致，於執行相同的有效位數為 FPU 註冊。 依預設會啟用安全的最佳化的縮寫，例如。 預設為停用例外狀況語意和 FPU 環境大小寫。

|fp： 精確語意|說明|
|-|-|
|捨入語意|在指派的明確捨入類型轉換和函式呼叫。 中繼運算式將評估在暫存器有效位數。|
|代數轉換|嚴格遵守非關聯、 非分散浮點代數，除非轉換保證在一律產生相同的結果。|
|縮寫|允許的預設值。 如需詳細資訊，請參閱 > 一節[fp_contract pragma](#the-fp-contract-pragma)。|
|浮點數的評估順序|編譯器可能會重新排列浮點運算式的評估，前提是最終的結果不會改變。|
|FPU 環境存取|預設為停用。 如需詳細資訊，請參閱 > 一節[fenv_access pragma](#the-fenv-access-pragma)。 假設的預設有效位數和捨入模式。|
|浮點例外狀況語意|預設為停用。 如需詳細資訊，請參閱[/fp： 除了](fp-specify-floating-point-behavior.md)。|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpprecise"></a>捨入下 fp 浮點運算式的語意： 精確

Fp： 精確的模型一定會執行在最高的實際有效位數，只在運算式評估中特定點上明確捨入的中繼計算。 四捨五入到指定使用者的有效位數一律會發生在四個位置: （a） 時進行指派時，（b） 的類型轉換執行時，（c） 浮點值傳遞時做為引數的函式和從傳回浮點值 （d）函式。 因為中繼計算一律會執行在暫存器有效位數，中繼結果的精確度是平台相依 (雖然會一律至少為指定的使用者為精確有效位數精確度)。

請考慮下列程式碼中的，指派運算式。 將在暫存器精確度計算右手邊的指派運算子 '=' 的運算式，並將其明確四捨五入指派的左側的型別。

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

若要明確捨入的中繼結果，導入 typecast。 例如，如果先前的程式碼修改新增的明確類型轉換，中繼運算式 (c * d) 將捨入 typecast 的類型。

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

一個併入此捨入的方法是，某些看似對等轉換實際上並沒有相同的語意。 例如，下列轉換會分割成兩個指派運算式的單一指派運算式。

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

這些編碼方式並沒有相等語意，因為第二個編碼有每個導入額外的指派作業，並因此額外圓點。

當函式傳回浮點值時，值會捨入至函式的類型。 當浮點數的值做為參數傳遞至函式時，將會捨入值的參數型別。 例如: 

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

### <a name="architecture-specific-rounding-under-fpprecise"></a>特定架構的捨入下 fp： 精確

|處理器|捨入中繼運算式的有效位數|
|-|-|
|x86|16 位元的指數所提供的延伸範圍，中繼運算式會計算在預設 53 位元有效位數。 當這些 53:16 值會 「 溢出 」 （如有可能會在函式呼叫） 的記憶體時，擴充的指數範圍會縮小為 11 個位元。 也就是說，餘力的值會轉換成標準的雙精確度格式與只 11 位元的指數。<br/>使用者可以切換到延伸的 64 位元精確度，藉由改變浮點控制字組使用中繼捨入`_controlfp`並啟用 FPU 環境存取 (請參閱[fenv_access pragma](#the-fenv-access-pragma))。 不過，擴充的有效位數的暫存器值會溢出到記憶體中，當中繼結果仍會四捨五入為雙精度。<br/>變更受限於這個特定語意。|
|amd64|在 amd64 FP 語意會與其他平台稍有不同。 基於效能考量，中繼的作業會計算在最寬的有效位數，而不是其中一個運算元，在可用的最大位數。  若要強制使用更多有效位數比運算元要計算的計算，使用者需要導入子運算式中至少一個運算元的轉換作業。<br/>變更受限於這個特定語意。|

### <a name="algebraic-transformations-under-fpprecise"></a>代數轉換之下 fp： 精確

當 fp： 精確模式已啟用，編譯器會永遠不會執行代數轉換*除非最終結果是可以證明相同*。 許多實際數字算術的熟悉代數規則請勿一律保留浮點算術。 例如，下列運算式是對等 Reals，但不是需要的浮點數。

|表單|描述|
|-|-|
|`(a+b)+c = a+(b+c)`|關聯規則新增|
|`(a*b)*c = a*(b*c)`|乘法的關聯規則|
|`a*(b+c) = a*b + b*c`|透過加入乘法的分佈|
|`(a+b)(a-b) = a*a-b*b`|代數分解|
|`a/b = a*(1/b)`|除數為乘法反元素|
|`a*1.0 = a`|乘法類單位的身分識別|

此函式簡介範例所示`KahanSum`，編譯器可能會想執行各種代數轉換，才可產生更快速的程式。 雖然最佳化依賴這類代數轉換幾乎都是不正確，但有它們是完全安全的情況。 比方說，則需要取代除以*常數*乘法逆元乘以常數的值：

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

這是安全的轉換因為最佳化工具可以判斷在編譯時期 x / 4.0 = = x*(1/4.0) 所有浮點值的 x，其包括無限大和 NaN。 透過取代乘法除法運算，編譯器可以儲存數個週期 — 尤其是對 FPUs 不會直接實作除法，但需要編譯器產生的對等近似值組合，並乘以-新增取得指示。 編譯器可能會執行這類最佳化下 fp： 精確取代乘法運算會產生精確時，才相同產生除法運算。 編譯器還會執行 trivial 轉換之下 fp: precise，提供完全相同的結果。 它們包括：

|表單|描述
|-|-|
|`(a+b) == (b+a)`|交替規則新增|
|`(a*b) == (b*a)`|乘法交替規則|
|`1.0*x*y == x*1.0*y == x*y*1.0 == x*y`|乘以 1.0 的乘法結果|
|`x/1.0*y == x*y/1.0 == x*y`|除以 1.0 的除法|
|`2.0*x == x+x`|乘法 2.0|

### <a name="contractions-under-fpprecise"></a>Fp 底下的縮寫： 精確

許多新型的浮點單位的主要架構功能會執行乘法，後面接著為具有任何中繼捨入錯誤的單一作業中的新加入的功能。 比方說，Intel 的 Itanium 架構會提供指示來結合這些三元運算，每個 (*b + c)，(* b c) 和 (c a * b)，到單一的浮點指令 (fma fms 和 fnma 分別)。 這些單一指示會比執行個別的速度快乘號和加入的指示，而且更正確因為沒有中繼進位的產品。 此最佳化可以大幅加速包含多項 multiply 交錯函式，並將作業加入。 例如，請考慮下列演算法會計算兩個 n 維向量的內積。

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

可以執行這項計算一系列的乘新增指示的格式為 p = p + x [i] * y [i]。

縮減最佳化可以個別控制使用`fp_contract`編譯器的 pragma。 根據預設，fp： 精確的模型可讓的縮寫，因為它們改善精確度和速度。 在 /fp: precise，編譯器會永遠不會合約具有明確的捨入的運算式。
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

### <a name="order-of-floating-point-expression-evaluation-under-fpprecise"></a>Fp 底下的浮點運算式評估的順序： 精確

保留的浮點運算式的評估順序的最佳化一律安全，因此所許可的 fp： 精確模式。 請考慮下列函式會計算出單一的有效位數中的兩個 n 維向量的內積。 下方的第一個程式碼區塊是原始函式程式設計人員，可能會編碼後面跟著相同的函式之後的部分迴圈 unrolling 最佳化。

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

此最佳化的主要優點是它減少的條件式迴圈分支數目，最多可達 75%。 此外，藉由增加在迴圈主體中的作業數目，編譯器現在可能會有更多的機會，以進一步最佳化。 比方說，有些 FPUs 或許可以執行乘新增在 p + = x [i] * y [i] 時同時擷取的值 [i + 1] x 和 y [i + 1] 的下一個步驟中使用。 這種類型是最佳化的用於浮點計算非常安全的因為它會保留作業的順序。

好處是，通常要重新排列整個作業，以產生更快的程式碼編譯器。 請考慮下列程式碼：

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

C + + 語意規則表示程式應該產生的結果，如同第一次計算 x 則 y 和 z 最後。 假設，編譯器必須只能有四個可用的浮點暫存器。 如果編譯器會強制計算 x、 y 和 z 順序，可能會選擇要產生程式碼與下列語法：

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

有數個清楚地重複的作業是這種編碼方式。 如果編譯器嚴格遵循 c + + 語意規則，這種排序，因為程式可能會存取將 FPU 環境之間每個指派。 不過，fp 的預設設定： 精確允許編譯器最佳化如同程式不會存取環境，讓它可以重新排列這些運算式。 然後，它是可用來移除重複計算三個值，以相反順序，如下：

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

這種編碼方式是可清楚地，具有 fp 指令數目減少幾乎 40%。 結果的 x、 y 和 z 都相同如往常一般，但計算較少負荷。

下 fp: precise，編譯器可能會也*交錯*通用子運算式，以產生更快的程式碼。 例如，程式碼以計算二次方程式方程式的根目錄可能會寫入，如下所示：

```cpp
double a, b, c, root0, root1;
...
root0 = (-b + sqrt(b*b-4*a*c))/(2*a);
root1 = (-b - sqrt(b*b-4*a*c))/(2*a);
```

雖然這些運算式差異只在單一作業，程式設計人員可能會撰寫以保證每個根值，會計算最高的實際精確度這種方式。 在 /fp: precise，編譯器就可以交錯 root0 和 root1 移除而不會遺失有效位數的通用子運算式的計算。 比方說，下列已移除多餘的幾個步驟時產生相同的答案。

```cpp
double a, b, c, root0, root1;
...
register tmp0 = -b;
register tmp1 = sqrt(b*b-4*a*c);
register tmp2 = 2*a;
root0 = (tmp0+tmp1)/tmp2;
root1 = (tmp0-tmp1)/tmp2;
```

其他最佳化可能會嘗試移動某些獨立運算式的評估。 請考慮下列演算法包含迴圈主體中條件式分支。

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

編譯器可能會偵測出運算式的值 (abs(d) > 1) 為迴圈主體內的非變異值。 這可讓編譯器在 」 找出"if 外部迴圈主體中，將上述程式碼轉換成下列陳述式：

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

在轉換之後，不再條件式分支中的迴圈主體，因此可大幅改善在迴圈的整體效能。 這種類型的最佳化是非常安全因為運算式評估 (abs(d) > 1.0) 是獨立於其他運算式。

如果存在 FPU 環境存取或浮點例外狀況，這些類型的最佳化被 contraindicated 因為他們變更語意的流程。 這種最佳化，才可以使用下 fp： 精確模式由於 FPU 環境存取和浮點例外狀況語意預設會停用。 函式會存取將 FPU 環境可以明確地使用停用這種最佳化`fenv_access`編譯器的 pragma。 同樣地，使用浮點例外狀況的函式應該使用`float_control(except ... )`編譯器 pragma (或使用 **/fp： 除了**命令列參數)。

在 [摘要] fp： 精確模式可讓編譯器重新排列浮點運算式的評估在條件，則不會改變的最終結果，但結果並未相依將 FPU 環境或浮點例外狀況。

### <a name="fpu-environment-access-under-fpprecise"></a>FPU 環境存取下 fp： 精確

當 fp： 精確模式已啟用，則編譯器會假設程式不會無法存取或修改將 FPU 環境。 如同稍早所述，這項假設可讓編譯器在重新排列或移動浮點作業，以改善效率下 fp： 精確。

有些程式可能會改變浮點捨入方向使用`_controlfp`函式。 比方說，有些程式計算上限和下限誤差界限上的算術運算執行相同的計算兩次，第一次時朝向負無限大方向捨入，然後同時捨入朝向正無限大。 由於 FPU 提供便利的方式來控制四捨五入，程式設計人員可以選擇變更會改變將 FPU 環境的捨入模式。 下列程式碼會計算所改變將 FPU 環境確切的錯誤繫結的浮點數的乘法。

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -&infin;
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );    // round to +&infin;
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

下 fp: precise，編譯器一律會假設預設 FPU 環境中，因此最佳化工具可以自由地忽略呼叫`_controlfp`並減少 cUpper 上述指派 = cLower = * b; 清楚，這會產生不正確的結果。 若要避免這種最佳化，請使用，FPU 環境存取啟用`fenv_access`編譯器的 pragma。

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

在 /fp: precise，重新排列運算式評估的最佳化可能會變更某些錯誤就會發生的點。 存取狀態字組的程式應該將 FPU 環境存取啟用使用`fenv_access`編譯器的 pragma。

如需詳細資訊，請參閱 > 一節[fenv_access pragma](#the-fenv-access-pragma)。

### <a name="floating-point-exception-semantics-under-fpprecise"></a>浮點例外狀況語意下 fp： 精確

根據預設，浮點例外狀況語意會停用下 fp： 精確。 大部分的 c + + 程式設計人員想要處理浮點數的例外狀況，而不使用系統或 c + + 例外狀況。 此外，如稍早所述，停用浮點例外狀況語意可讓編譯器更大的彈性時最佳化浮點運算。 使用 **/fp： 除了**切換或`float_control`pragma，來使用 fp 時啟用浮點例外狀況語意： 精確的模型。

如需詳細資訊，請參閱 > 一節[啟用浮點例外狀況語意](#enabling-floating-point-exception-semantics)。

## <a name="the-fpfast-mode-for-floating-point-semantics"></a>浮點語意: fast 模式

啟用： fast 模式時，編譯器會放寬規則該 fp： 精確時所使用最佳化浮點運算。 這個模式就可讓編譯器在進一步最佳化浮點程式碼的速度，但會犧牲浮點數的準確度和正確性。 請勿依賴高度精確的計算浮點數的程式可能會遇到速度顯著改進啟用： fast 模式。

使用啟用： fast 浮點模式[/fp: fast](fp-specify-floating-point-behavior.md)命令列編譯器參數，如下所示：

> cl /fp: fast source.cpp

此範例會指示編譯器產生 source.cpp 檔的程式碼時，使用： fast 語意。 : Fast 模型可以也叫用函式的函式使用`float_control`編譯器的 pragma。

如需詳細資訊，請參閱 > 一節[float_control pragma](#the-float-control-pragma)。

在： fast 模式下，編譯器可能會執行 alter 浮點計算精確度的最佳化。 編譯器可能會不正確捨入在指派、 類型轉換或函式呼叫，並將中繼捨入不一定會執行。 一定會啟用的縮寫，例如浮點的特定最佳化。 浮點例外狀況語意和 FPU 環境敏感度是停用，無法使用。

|: fast 語意|說明
|-|-|
|捨入語意|在指派的明確捨入類型轉換和函式呼叫可能會被忽略。<br/>在少於註冊根據效能需求的有效位數，可能會捨入中繼運算式。|
|代數轉換|編譯器可能會轉換運算式，根據實際數字關聯、 分散代數;這些轉換不保證精確度或正確。|
|縮寫|永遠啟用。無法停用的 pragma `fp_contract`|
|浮點數的評估順序|編譯器可能會重新排列浮點運算式，評估，即使這類變更可能會改變的最終結果。|
|FPU 環境存取|已停用。 無法使用|
|浮點例外狀況語意|已停用。 無法使用|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpfast"></a>捨入下： fast 的浮點運算式的語意

不同於 fp： 精確的模型，： fast 模型執行中繼計算在最方便的有效位數。 在指派，捨入的類型轉換和函式呼叫可能不一定會發生。 比方說，第一個函式的下列導入三個單精確度變數 (`C`，`Y`和`T`)。 編譯器可能會選擇低落這些變數時，作用中的型別提升`C`，`Y`和`T`到雙精確度。

原始函式：

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

在此範例中，： fast 具有 subverted 原始函式的目的。 最終最佳化結果，該變數中保存`sum`，可能會相當： 從正確的結果。

底下： fast，編譯器通常會至少維護原始碼所指定的精確度。 不過，在某些情況下，編譯器可選擇加以執行中繼運算式*降低有效位數*比在原始程式碼中所指定。 例如，以下的第一個程式碼區塊呼叫平方根函式的雙精確度版本。 在： fast，在某些情況下，例如當的結果與運算元的函式會明確轉換成單精確度，編譯器可能會選擇雙精確度的呼叫取代`sqrt`單精確度呼叫`sqrtf`函式。 因為確保進入值轉型`sqrt`和傳出的值會捨入為單精確度，這只會變更的捨入的位置。 如果進入 sqrt 的值是雙精度值，而編譯器執行此轉換，最多有一半的精確度位元可能是錯誤。

原始函式

```cpp
double sqrt(double);
// . . .
double a, b, c;
float f1, f2;
// . . .
float length = (float)sqrt((float)(a*a + b*b + c*c));
float sum = (float) ((double)f1 + (double)f2);
```

最佳化的函式

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

雖然較不精確，此最佳化可能會特別有幫助，提供單一有效位數，內建函式版本，例如處理器為目標時`sqrt`。 只要精確時，編譯器會使用這種最佳化是平台和內容相依。

此外，為中繼計算，可能會執行任何可供編譯器的有效位數層級的有效位數不保證的一致性。 編譯器會嘗試維持最少的程式碼所指定的有效位數層級，但： fast 會讓最佳化工具仍會向下轉型中繼計算以產生更快或較小的機器碼。 比方說，編譯器可能會進一步要捨入為單精確度中繼乘法的某些最佳化從上方的程式碼。

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

這種捨入的其他可能因使用較低精確度浮點數單位，例如 SSE2，執行某些中繼計算。 所以平台相依;: fast 四捨五入的精確度。一個處理器用於編譯的程式碼可能不一定適用於另一個處理器。 它會保持給使用者，以便判斷是否速度優點遠大於任何精確度的問題。

如果當做特定函數特別有問題： fast 最佳化，浮點模式可以從本機切換到 fp： 精確使用`float_control`編譯器的 pragma。


### <a name="algebraic-transformations-under-fpfast"></a>底下： fast 代數轉換

: Fast 模式可讓編譯器執行特定、 不安全的代數轉換，到浮點點運算式。 例如，下列不安全的最佳化，您可能必須使用： fast 底下。

||||
|-|-|-|
|原始的程式碼|步驟 1|步驟 2
|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = y – a – b;`<br/><br/>`c = x – z;`<br/><br/>`c = x * z;`<br/><br/>`c = x - z;`<br/><br/>`c = x + z;`<br/><br/>`c = z-x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x – 0;`<br/><br/>`c = x * 0;`<br/><br/>`c = x - 0;`<br/><br/>`c = x + 0;`<br/><br/>`c = 0 - x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x;`<br/><br/>`c = 0;`<br/><br/>`c = x;`<br/><br/>`c = x;`<br/><br/>`c = -x;`|

在步驟 1 中，編譯器會觀察的`z = y – a – b`會一律等於零。 雖然技術上而言是無效的觀察，它允許： fast 底下。 然後，編譯器會傳播常數零值到變數 z 的每個後續使用。 在步驟 2 中，編譯器進一步最佳化，觀察`x - 0 == x`，`x * 0 == 0`等等。同樣地，即使這些觀察後不嚴格有效，它們所許可： fast 的。 最佳化程式碼現在會更快，但也可能是較不精確或甚至不正確。

啟用： fast 模式時，您可能必須使用任何下列的 （不安全） 代數規則最佳化工具：

|||
|-|-|
|表單|描述|
|`(a + b) + c = a + (b + c)`|關聯規則新增|
|`(a * b) * c = a * (b * c)`|乘法的關聯規則|
|`a * (b + c) = a * b + b * c`|透過加入乘法的分佈|
|`(a + b)(a - b) = a * a - b * b`|代數分解|
|`a / b = a * (1 / b)`|除數為乘法反元素|
|`a * 1.0 = a, a / 1.0 = a`|乘法類單位的身分識別|
|`a ± 0.0 = a, 0.0 - a = -a`|加法類身分識別|
|`a / a = 1.0, a - a = 0.0`|取消|

如果： fast 最佳化會特別有問題的特定函式，浮點模式可以從本機切換到 fp： 精確使用`float_control`編譯器的 pragma。

### <a name="order-of-floating-point-expression-evaluation-under-fpfast"></a>: Fast 底下的浮點運算式評估的順序

不同於 /fp: precise，： fast 允許編譯器在重新排列以產生更快的程式碼的浮點運算。 因此，某些最佳化： fast 下的可能不會保留運算式的預期的順序。 例如，請考慮下列函式，會計算兩個 n 維向量的內積。

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

底下： fast，最佳化工具可能會執行的純量減少`dotProduct`函式有效地轉換函式，如下所示：

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

最佳化版本的函式在四個不同的產品就會同時採用，然後再加在一起。 此最佳化可以加速，以計算`dotProduct`所最多為四根據目標處理器，但最終結果的因素可能因此錯誤而使它。 如果這種最佳化單一函式或轉譯單位特別有問題，浮點模式可以從本機切換到 fp： 精確使用`float_control`編譯器的 pragma。

## <a name="the-fpstrict-mode-for-floating-point-semantics"></a>/Fp: strict 模式浮點語意

時 /fp: strict 模式已啟用，編譯器遵守所有相同規則該 fp： 精確時所使用最佳化浮點運算。 這個模式也會啟用浮點例外狀況語意以及將 FPU 環境的敏感度，並且會停用某些最佳化功能，例如的縮寫。 它是作業的最嚴格模式。

/Fp: strict 浮點模式會使用啟用[/fp: strict](fp-specify-floating-point-behavior.md) ，如下所示的命令列編譯器參數：

> cl /fp: strict source.cpp

此範例指示編譯器使用 /fp: strict 語意產生 source.cpp 檔的程式碼時。 /Fp: strict 模型可以也叫用函式的函式使用`float_control`編譯器的 pragma。

如需詳細資訊，請參閱 > 一節[float_control pragma](#the-float-control-pragma)。

在 /fp: strict 模式下，編譯器永遠不會執行任何擾亂浮點計算精確度的最佳化。 編譯器一律會在指派正確無條件、 類型轉換和函式呼叫，且中繼捨入會一致，於執行相同的有效位數為 FPU 註冊。 預設會啟用浮點例外狀況語意和 FPU 環境大小寫。 已停用某些最佳化功能的縮寫，例如，因為編譯器無法保證正確性，在每個案例。

|/fp: strict 語意|說明|
|-|-|
|捨入語意|在指派的明確捨入類型轉換和函式呼叫<br/>中繼運算式將評估在暫存器有效位數。<br/>相同 fp： 精確|
|代數轉換|嚴格遵守非關聯、 非分散浮點代數，除非轉換保證在一律產生相同的結果。<br/>相同 fp： 精確|
|縮寫|一律停用|
|浮點數的評估順序|編譯器不會重新排列浮點運算式的評估|
|FPU 環境存取|一定會啟用。|
|浮點例外狀況語意|預設為啟用。|

### <a name="floating-point-exception-semantics-under-fpstrict"></a>浮點例外狀況語意下 fp: strict

根據預設，在 fp 啟用浮點例外狀況語意： strict 模型。 若要停用這些語意，請使用 **/fp： 除了-** 切換或引進`float_control(except, off)`pragma。

如需詳細資訊，請參閱章節[啟用浮點例外狀況語意](#enabling-floating-point-exception-semantics)和[float_control Pragma](#the-float-control-pragma)。

## <a name="the-fenvaccess-pragma"></a>Fenv_access pragma

使用方式：

```cpp
#pragma fenv_access( [ on  | off ] )
```

[Fenv_access](../../preprocessor/fenv-access.md) pragma 可讓編譯器將 FPU 旗標測試和 FPU 模式變更可能會破壞的某些最佳化功能。 當狀態`fenv_access`停用時，編譯器就可以假設預設 FPU 模式才有效，並不會測試 FPU 旗標。 根據預設，環境存取已停用 fp： 精確模式，但它可能會明確地啟用使用這個 pragma。 在 /fp: strict，`fenv_access`永遠啟用，而且無法停用。 底下： fast，`fenv_access`一律停用，所以無法加以啟用。

Fp 中所述： 精確 區段中，某些程式設計人員可能會改變浮點捨入方向使用`_controlfp`函式。 比方說，若要計算上限和下限誤差界限上的算術運算，有些程式執行相同的計算兩次，第一次在捨入朝向負無限大，然後捨入朝向正無限大時。 由於 FPU 提供便利的方式來控制四捨五入，程式設計人員可以選擇變更會改變將 FPU 環境的捨入模式。 下列程式碼會計算所改變將 FPU 環境確切的錯誤繫結的浮點數的乘法。

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -infinity
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );       // round to +infinity
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

停用時， `fenv_access` pragma 可讓編譯器来假設預設 FPU 環境; 因此，最佳化工具是可用來忽略呼叫`_controlfp`並降低上述指派`cUpper = cLower = a*b`。 不過，啟用`fenv_access`可防止這種最佳化。

程式可能也會檢查 FPU 狀態字組，來偵測特定浮點數的錯誤。 例如，下列程式碼會檢查除以零和精確狀況

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

當`fenv_access`是停用，編譯器可能會重新排列的執行順序的浮點運算式，因此可能 subverting 將 FPU 狀態檢查。 啟用`fenv_access`可防止這種最佳化。

## <a name="the-fpcontract-pragma"></a>Fp_contract pragma

使用方式：

```cpp
#pragma fp_contract( [ on | off ] )
```

Fp 中所述： 精確區段中，縮減是許多新型的浮點單位的基本架構功能。 縮寫提供執行乘法，後面接著為具有任何中繼捨入錯誤的單一作業中的新加入的功能。 這些單一指示會比執行個別的速度快乘號和加入的指示，而且更正確因為沒有中繼進位的產品。 合約的作業可以計算的值`(a*b+c)`這兩項作業就如同一般計算為無限的精確度，而且就會四捨五入至最接近的浮點數。 此最佳化可以大幅加速包含多項 multiply 交錯函式，並將作業加入。 例如，請考慮下列演算法會計算兩個 n 維向量的內積。

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

可以執行這項計算一系列的乘加入表單的指示`p = p + x[i]*y[i]`。

[Fp_contract](../../preprocessor/fp-contract.md) pragma 可讓您指定是否可以縮減浮點運算式。 根據預設，fp： 精確模式可讓的縮寫，因為它們改善精確度和速度。 縮寫一定會啟用： fast 模式。 不過，因為縮寫可破壞明確的錯誤狀況，偵測`fp_contract`pragma 一律停用下 fp: strict 模式。 可能是運算式的範例收縮時`fp_contract`pragma 已啟用：

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

**/Fp： 精確**， **/fp: fast**， **/fp: strict**和 **/fp： 除了**參數控制浮點語意上的檔案基準。 [Float_control](../../preprocessor/float-control.md) pragma 提供這類函式的函式為基礎的控制項。

使用方式：

```cpp
#pragma float_control(push)
#pragma float_control(pop)
#pragma float_control( precise, on | off [, push] )
#pragma float_control( except, on | off [, push] )
```

Pragma`float_control(push)`和`float_control(pop)`分別 push 和 pop 的浮點數的模式和至堆疊的例外狀況 選項的目前狀態。 請注意，狀態`fenv_access`和`fp_contract`pragma 不會受到`pragma float_control(push/pop)`。

呼叫 pragma`float_control(precise, on)`會啟用和`float_control(precise, off)`將會停用精確模式語意。 同樣地，pragma`float_control(except, on)`會啟用和`float_control(except, off)`將會停用例外狀況語意。 只有精確語意也會啟用時，才可以啟用例外狀況語意。 當選擇性`push`引數已存在，狀態`float_control`變更語意之前推入選項。

### <a name="setting-the-floating-point-semantic-mode-on-a-function-by-function-basis"></a>設定浮點語意模式函式的函式為基礎

命令列參數，實際上是設定四個不同的浮點 pragma 的速記。 若要明確地選擇特定的浮點語意模式函式的函式為基礎，選取每四個浮點數選項 pragma 下表中所述：

||||||
|-|-|-|-|-|
||float_control(precise)|float_control(except)|fp_contract|fenv_access|
|/fp: strict|於|於|關閉|於|
|/fp: strict /fp： 除了-|於|關閉|關閉|於|
|/fp： 精確|於|關閉|於|關閉|
|/fp: precise /fp： 除外|於|於|於|關閉|
|/fp: fast|關閉|關閉|於|關閉|

例如，下列明確啟用： fast 語意。

```cpp
#pragma float_control( except, off )   // disable exception semantics
#pragma float_control( precise, off )  // disable precise semantics
#pragma fp_contract(on)                // enable contractions
#pragma fenv_access(off)               // disable fpu environment sensitivity
```

> [!Note]
> 例外狀況語意必須關閉之前關閉"precise"語意。

## <a name="enabling-floating-point-exception-semantics"></a>啟用浮點例外狀況語意

特定例外狀況的浮點條件，例如除以零，可能會導致 FPU 發出信號的硬體例外狀況。 預設為停用浮點例外狀況。 藉由修改 FPU 控制字組，以啟用浮點例外狀況`_controlfp`函式。 例如，下列程式碼可讓除以零的浮點例外狀況：

```cpp
_clearfp(); // always call _clearfp before
            // enabling/unmasking a FPU exception
_controlfp( _EM_ZERODIVIDE, _MCW_EM );
```

啟用除以零的例外狀況時，其分母等同於零的任何除法運算會導致發出信號 FPU 例外狀況。

若要將 FPU 控制字組，還原預設模式，請呼叫`_controlfp(_CW_DEFAULT, ~0)`。

啟用浮點例外狀況語意與 **/fp： 除了**旗標不同時啟用浮點例外狀況。 啟用浮點例外狀況語意時，編譯器必須承擔任何浮點運算可能會擲回例外狀況的可能性。 由於 FPU 是另一個處理處理器單元，可以與其他單元上的指示執行 FPU 上執行的指示。

啟用浮點例外狀況時，FPU 將暫止執行造成問題的指示的然後將 FPU 狀態字組表示例外狀況。 當 CPU 到達下一個浮點指令時，它會先檢查任何暫止 FPU 例外狀況。 如果沒有擱置中的例外狀況，處理器就會對它藉由呼叫作業系統所提供的例外狀況處理常式。 這表示，當浮點運算遇到例外狀況時，對應的例外狀況將偵測不到下一個浮點作業執行之前。 例如，下列程式碼所截獲除以零的例外狀況：

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

如果運算式中就會發生除以零狀況 = b/c，FPU 將不會設陷/引發的例外狀況，直到下一步的浮點運算運算式 2.0 中 * b。 這會產生下列輸出：

```Output
This line shouldn't be reached when c==0.0
SEH Exception Detected
```

對應至輸出的第一行 printf 應該尚未達到;它已達到因為浮點運算式 b/c 所造成的例外狀況未引發之前執行達到 2.0 * b。 若要引發的例外狀況之後執行 b/c，編譯器必須引入"wait":

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

此 「 等候 」 的指示會強制處理器將 FPU 的狀態同步處理，並處理任何擱置中的例外狀況。 編譯器只會產生這些 「 等候 」 指示時啟用浮點語意。 當停用這些語意，因為沒有依預設時，程式可能會遇到同步性錯誤，類似上述項目，使用浮點例外狀況時。

啟用浮點語意時，編譯器不只會將"wait"指示，它也會防止編譯器錯誤地最佳化浮點程式碼有可能的例外狀況的情況下。 這包括任何 alter 例外狀況擲回的點的轉換。 這些因素，因為啟用浮點語意可能會大幅減少因此降低應用程式的效能產生機器碼的效率。

下 fp 預設會啟用浮點例外狀況語意： strict 模式。 若要啟用這些語意中 fp： 精確模式中，加入 **/fp： 除了**切換到命令列編譯器。 浮點例外狀況語意可以也啟用和停用函式的函式使用`float_control`pragma。

### <a name="floating-point-exceptions-as-c-exceptions"></a>為 c + + 例外狀況的浮點例外狀況

為所有的硬體例外狀況，浮點例外狀況不在本質上會造成 c + + 例外狀況，但改為觸發結構化例外狀況。 若要以 c + + 例外狀況對應結構化的浮點例外狀況，使用者可能會導致自訂 SEH 例外狀況轉譯器。 首先，會對應至每個浮點例外狀況的 c + + 例外狀況：

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

然後，導入轉譯函式，將會偵測浮點數的 SEH 例外狀況並擲回對應的 c + + 例外狀況。 若要使用此函式，設定目前的處理序執行緒使用結構化例外狀況處理常式轉譯程式[_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)函式的執行階段程式庫。

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

一旦完成初始化此對應，浮點例外狀況的行為就好像它們是 c + + 例外狀況。 例如: 

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
