---
title: '&lt;random&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 08/24/2017
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <random>
dev_langs:
- C++
helpviewer_keywords:
- random header
ms.assetid: 60afc25c-b162-4811-97c1-1b65398d4c57
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdfae58c03d18638ad44f844909d585b41d710cd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862906"
---
# <a name="ltrandomgt"></a>&lt;random&gt;

定義亂數產生工具，允許建立統一分佈的亂數。

## <a name="syntax"></a>語法

```cpp
#include <random>
```

## <a name="summary"></a>總結

「亂數產生器」是一個物件，可產生一連串的虛擬隨機值。 產生統一分佈於指定範圍之值的產生器是「統一亂數產生器」(Uniform Random Number Generator，URNG)。 設計成當作 URNG 功能的樣板類別稱為「引擎」，如果該類別具有特定一般特性的話 (本文稍後會予以討論)。 一般而言，URNG 可以與「分佈」合併使用，方法是將 URNG 做為引數傳遞至分佈的 `operator()`，以產生由分佈所定義的方式而分佈的值。

這些連結會跳到本文的主要小節：

- [範例](#code)

- [分類清單](#listing)

- [引擎和分佈](#engdist)

- [備註](#comments)

### <a name="quick-tips"></a>快速提示

以下是使用時，請記住一些秘訣\<隨機 >:

- 在大部分的用途中，URNG 都會產生必須由分佈所圖形化的原始位元 (需要注意的例外狀況是 [std::shuffle()](../standard-library/algorithm-functions.md#shuffle)，原因是它直接使用 URNG)。

- 因為執行 URNG 或分佈是修改作業，所以無法安全地同時呼叫 URNG 或分佈的單一具現化。 如需詳細資訊，請參閱 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)。

- 提供數個引擎的[預先定義 typedef](#typedefs)；如果使用引擎，這是建立 URNG 的慣用方式。

- 大部分應用程式的最實用配對是 `mt19937` 引擎搭配 `uniform_int_distribution` (如本文稍後的[程式碼範例](#code)所示)。

有許多選項可以選擇在\<隨機 > 標頭，而且其中任何最好過期的 C 執行階段函式是`rand()`。 如需相關問題資訊`rand()`以及\<隨機 > 解決這些缺點，請參閱[這段影片](http://go.microsoft.com/fwlink/p/?linkid=397615)。

## <a name="code"></a> 範例

下列程式碼範例示範如何產生一些亂數，在此情況下，其中有五個使用以不具決定性的種子建立的產生器。

```cpp
#include <random>
#include <iostream>

using namespace std;

int main()
{
    random_device rd;   // non-deterministic generator
    mt19937 gen(rd());  // to seed mersenne twister.
                        // replace the call to rd() with a
                        // constant value to get repeatable
                        // results.

    for (int i = 0; i < 5; ++i) {
        cout << gen() << " "; // print the raw output of the generator.
    }
    cout << endl;
}
```

```Output
2430338871 3531691818 2723770500 3252414483 3632920437
```

雖然這些是高品質的亂數，且在每次執行此程式時都會不同，卻不一定在有用的範圍內。 若要控制範圍，請使用平均分佈，如下列程式碼所示：

```cpp
#include <random>
#include <iostream>

using namespace std;

int main()
{
    random_device rd;   // non-deterministic generator
    mt19937 gen(rd());  // to seed mersenne twister.
    uniform_int_distribution<> dist(1,6); // distribute results between 1 and 6 inclusive.

    for (int i = 0; i < 5; ++i) {
        cout << dist(gen) << " "; // pass the generator to the distribution.
    }
    cout << endl;
}
```

```Output
5 1 6 1 2
```

下一個程式碼範例會使用隨機播放向量和陣列之內容的平均分佈亂數產生器，示範較實際的使用情況。

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <array>
#include <iostream>
#include <random>
#include <string>
#include <vector>
#include <functional> // ref()

using namespace std;

template <typename C> void print(const C& c) {
    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

template <class URNG>
void test(URNG& urng) {

    // Uniform distribution used with a vector
    // Distribution is [-5, 5] inclusive
    uniform_int_distribution<int> dist(-5, 5);
    vector<int> v;

    for (int i = 0; i < 20; ++i) {
        v.push_back(dist(urng));
    }

    cout << "Randomized vector: ";
    print(v);

    // Shuffle an array
    // (Notice that shuffle() takes a URNG, not a distribution)
    array<string, 26> arr = { { "H", "He", "Li", "Be", "B", "C", "N", "O", "F",
        "Ne", "Na", "Mg", "Al", "Si", "P", "S", "Cl", "Ar", "K", "Ca", "Sc",
        "Ti", "V", "Cr", "Mn", "Fe" } };

    shuffle(arr.begin(), arr.end(), urng);

    cout << "Randomized array: ";
    print(arr);
    cout << "--" << endl;
}

int main()
{
    // First run: non-seedable, non-deterministic URNG random_device
    // Slower but crypto-secure and non-repeatable.
    random_device rd;
    cout << "Using random_device URNG:" << endl;
    test(rd);

    // Second run: simple integer seed, repeatable results
    cout << "Using constant-seed mersenne twister URNG:" << endl;
    mt19937 engine1(12345);
    test(engine1);

    // Third run: random_device as a seed, different each run
    // (Desirable for most purposes)
    cout << "Using non-deterministic-seed mersenne twister URNG:" << endl;
    mt19937 engine2(rd());
    test(engine2);

    // Fourth run: "warm-up" sequence as a seed, different each run
    // (Advanced uses, allows more than 32 bits of randomness)
    cout << "Using non-deterministic-seed \"warm-up\" sequence mersenne twister URNG:" << endl;
    array<unsigned int, mt19937::state_size> seed_data;
    generate_n(seed_data.begin(), seed_data.size(), ref(rd));
    seed_seq seq(begin(seed_data), end(seed_data));
    mt19937 engine3(seq);
    test(engine3);
}
```

```Output
Using random_device URNG:
Randomized vector: 5 -4 2 3 0 5 -2 0 4 2 -1 2 -4 -3 1 4 4 1 2 -2
Randomized array: O Li V K C Ti N Mg Ne Sc Cl B Cr Mn Ca Al F P Na Be Si Ar Fe S He H
--
Using constant-seed mersenne twister URNG:
Randomized vector: 3 -1 -5 0 0 5 3 -4 -3 -4 1 -3 0 -3 -2 -4 5 1 -1 -1
Randomized array: Al O Ne Si Na Be C N Cr Mn H V F Sc Mg Fe K Ca S Ti B P Ar Cl Li He
--
Using non-deterministic-seed mersenne twister URNG:
Randomized vector: 5 -4 0 2 1 -2 4 4 -4 0 0 4 -5 4 -5 -1 -3 0 0 3
Randomized array: Si Fe Al Ar Na P B Sc H F Mg Li C Ti He N Mn Be O Ca Cr V K Ne Cl S
--
Using non-deterministic-seed "warm-up" sequence mersenne twister URNG:
Randomized vector: -1 3 -2 4 1 3 0 -5 5 -5 0 0 5 0 -3 3 -4 2 5 0
Randomized array: Si C Sc H Na O S Cr K Li Al Ti Cl B Mn He Fe Ne Be Ar V P Ca N Mg F
--
```

此程式碼使用測試範本函式，示範兩個不同的隨機：隨機化整數向量，並隨機播放已編製索引資料的陣列。 測試函式的第一次呼叫會使用具有加密保護，且不具決定性、不可植入、不可重複的 URNG `random_device`。 第二個測試回合使用 `mersenne_twister_engine` 做為 URNG，並搭配決定性 32 位元常數種子，這表示結果是可重複的。 第三個測試回合將來自 `mersenne_twister_engine` 的32 位元不具決定性結果植入 `random_device`。 第四個測試回合透過使用填入 `random_device` 結果的[種子序列](../standard-library/seed-seq-class.md)，將此情況延伸，這可以有效地提供比 32 位元更多的不具決定性隨機性 (但還是不具加密保護)。 如需詳細資訊，請繼續閱讀本文。

## <a name="listing"></a> 分類清單

###  <a name="urngs"></a> 統一亂數產生器

通常會根據這些屬性描述 URNG：

1. **期間長度**：它使用多少個反覆項目來重複一串產生的數字序列。 愈長愈好。

2. **效能**：產生數字的速度，以及使用多少記憶體。 愈小愈好。

3. **品質**：產生的序列有多接近真正亂數。 這通常稱為「隨機性」。

下列章節會列出統一亂數產生器 (Urng) 中提供\<隨機 > 標頭。

####  <a name="rd"></a> 不具決定性產生器

|||
|-|-|
|[random_device 類別](../standard-library/random-device-class.md)|使用外部裝置，產生不具決定性且以加密編譯方式保護的隨機序列。 通常用於植入引擎。 低效能，品質很高。 如需詳細資訊，請參閱[備註](#comments)。|

####  <a name="typedefs"></a> 具有預先定義參數的引擎 Typedef

用於具現化引擎和引擎配接器。 如需詳細資訊，請參閱[引擎和分佈](#engdist)。

- `default_random_engine`：預設的引擎。
 `typedef mt19937 default_random_engine;`

- `knuth_b`：Knuth 引擎。
 `typedef shuffle_order_engine<minstd_rand0, 256> knuth_b;`

- `minstd_rand0`：1988 最低標準引擎 (Lewis、Goodman 及 Miller，1969 年)。
 `typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;`

- `minstd_rand`：更新的最低標準引擎 `minstd_rand0` (Park、Miller 及 Stockmeyer，1993 年)。
 `typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;`

- `mt19937`：32 位元梅森旋轉引擎 (Matsumoto 和 Nishimura，1998 年)。
 `typedef mersenne_twister_engine<unsigned int, 32, 624, 397,      31, 0x9908b0df,      11, 0xffffffff,      7, 0x9d2c5680,      15, 0xefc60000,      18, 1812433253> mt19937;`

- `mt19937_64`：64 位元梅森旋轉引擎 (Matsumoto 和 Nishimura，2000 年)。
 `typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,      31, 0xb5026f5aa96619e9ULL,      29, 0x5555555555555555ULL,      17, 0x71d67fffeda60000ULL,      37, 0xfff7eee000000000ULL,      43, 6364136223846793005ULL> mt19937_64;`

- `ranlux24` 24 位元 RANLUX 引擎 （Martin Lüscher 和 Fred James，1994 年）。
 `typedef discard_block_engine<ranlux24_base, 223, 23> ranlux24;`

- `ranlux24_base`：用做 `ranlux24` 的基底。
 `typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`

- `ranlux48` 48 位元 RANLUX 引擎 （Martin Lüscher 和 Fred James，1994 年）。
 `typedef discard_block_engine<ranlux48_base, 389, 11> ranlux48;`

- `ranlux48_base`：用做 `ranlux48` 的基底。
 `typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`

####  <a name="eng"></a> 引擎範本

引擎範本用做獨立 URNG，或用做傳遞給[引擎配接器](#engadapt)的基底引擎。 這些通常使用[預先定義的引擎 typedef](#typedefs) 進行具現化，並傳遞給[分佈](#distributions)。 如需詳細資訊，請參閱[引擎和分佈](#engdist)一節。

|||
|-|-|
|[linear_congruential_engine 類別](../standard-library/linear-congruential-engine-class.md)|使用線性同餘演算法，產生隨機序列。 最為簡單且品質最低。|
|[mersenne_twister_engine 類別](../standard-library/mersenne-twister-engine-class.md)|使用梅森旋轉演算法，產生隨機序列。 最為複雜，但品質最高 (random_device 類別除外)。 效能極為快速。|
|[subtract_with_carry_engine 類別](../standard-library/subtract-with-carry-engine-class.md)|使用帶進位減法演算法，以產生隨機序列。 改善 `linear_congruential_engine`，但是品質和效能比 `mersenne_twister_engine` 還要低。|

####  <a name="engadapt"></a> 引擎配接器範本

引擎配接器是可配接其他 (基底) 引擎的範本。 這些通常使用[預先定義的引擎 typedef](#typedefs) 進行具現化，並傳遞給[分佈](#distributions)。 如需詳細資訊，請參閱[引擎和分佈](#engdist)一節。

|||
|-|-|
|[discard_block_engine 類別](../standard-library/discard-block-engine-class.md)|捨棄其基底引擎所傳回的值，以產生隨機序列。|
|[independent_bits_engine 類別](../standard-library/independent-bits-engine-class.md)|重新封裝其基底引擎所傳回之值的位元，以產生具有指定位元數的隨機序列。|
|[shuffle_order_engine 類別](../standard-library/shuffle-order-engine-class.md)|透過重新排列基底引擎傳回的值產生隨機序列。|

[[引擎範本](#eng)]

###  <a name="distributions"></a> 亂數分佈

下列章節會列出中提供的分佈\<隨機 > 標頭。 分佈是一個後續處理機制，通常使用 URNG 輸出做為輸入，並透過定義的統計可能性密度函式來散發輸出。 如需詳細資訊，請參閱[引擎和分佈](#engdist)一節。

#### <a name="uniform-distributions"></a>統一分佈

|||
|-|-|
|[uniform_int_distribution 類別](../standard-library/uniform-int-distribution-class.md)|產生跨封閉間隔 \[a, b] (內含 - 內含) 中某個範圍的統一整數值分佈。|
|[uniform_real_distribution 類別](../standard-library/uniform-real-distribution-class.md)|產生跨半開間隔 [a, b) (內含 - 排除) 中某個範圍的統一實數 (浮點) 值分佈。|
|[generate_canonical](../standard-library/random-functions.md#generate_canonical)|產生跨 [0, 1) (內含 - 排除) 之指定精確度的實數 (浮點) 值平均分佈。|

[[亂數分佈](#distributions)]

#### <a name="bernoulli-distributions"></a>白努利分佈

|||
|-|-|
|[bernoulli_distribution 類別](../standard-library/bernoulli-distribution-class.md)|產生 `bool` 值的白努利分佈。|
|[binomial_distribution 類別](../standard-library/binomial-distribution-class.md)|產生整數值的二項式分佈。|
|[geometric_distribution 類別](../standard-library/geometric-distribution-class.md)|產生整數值的幾何分佈。|
|[negative_binomial_distribution 類別](../standard-library/negative-binomial-distribution-class.md)|產生整數值的負二項式分佈。|

[[亂數分佈](#distributions)]

#### <a name="normal-distributions"></a>常態分佈

|||
|-|-|
|[cauchy_distribution 類別](../standard-library/cauchy-distribution-class.md)|產生實數 (浮點) 值的柯西分佈。|
|[chi_squared_distribution 類別](../standard-library/chi-squared-distribution-class.md)|產生實數 (浮點) 值的卡方分佈。|
|[fisher_f_distribution 類別](../standard-library/fisher-f-distribution-class.md)|產生的 F 分佈 （也稱為 Snedecor 的 F 分佈或費雪 Snedecor 分佈） 實數 （浮點） 值。|
|[lognormal_distribution 類別](../standard-library/lognormal-distribution-class.md)|產生實數 (浮點) 值的對數常態分佈。|
|[normal_distribution 類別](../standard-library/normal-distribution-class.md)|產生實數 (浮點) 值的常態 (高斯) 分佈。|
|[student_t_distribution 類別](../standard-library/student-t-distribution-class.md)|產生實數 (浮點) 值的學生 *t* 分佈。|

[[亂數分佈](#distributions)]

#### <a name="poisson-distributions"></a>波氏分佈

|||
|-|-|
|[exponential_distribution 類別](../standard-library/exponential-distribution-class.md)|產生實數 (浮點) 值的指數分佈。|
|[extreme_value_distribution 類別](../standard-library/extreme-value-distribution-class.md)|產生實數 (浮點) 值的極值分佈。|
|[gamma_distribution 類別](../standard-library/gamma-distribution-class.md)|產生實數 (浮點) 值的 Gamma 分佈。|
|[poisson_distribution 類別](../standard-library/poisson-distribution-class.md)|產生整數值的波氏分佈。|
|[weibull_distribution 類別](../standard-library/weibull-distribution-class.md)|產生實數 (浮點) 值的 Weibull 分佈。|

[[亂數分佈](#distributions)]

#### <a name="sampling-distributions"></a>取樣分佈

|||
|-|-|
|[discrete_distribution 類別](../standard-library/discrete-distribution-class.md)|產生離散整數分佈。|
|[piecewise_constant_distribution 類別](../standard-library/piecewise-constant-distribution-class.md)|產生實數 (浮點) 值的分段常數分佈。|
|[piecewise_linear_distribution 類別](../standard-library/piecewise-linear-distribution-class.md)|產生實數 (浮點) 值的分段線性分佈。|

[[亂數分佈](#distributions)]

### <a name="utility-functions"></a>公用程式函式

此區段會列出所提供的一般公用程式函數\<隨機 > 標頭。

|||
|-|-|
|[seed_seq 類別](../standard-library/seed-seq-class.md)|產生無偏差干擾種子序列。 用來避免複寫隨機變量資料流。 從引擎具現化許多 URNG 時十分有用。|

### <a name="operators"></a>運算子

此區段會列出中提供的運算子\<隨機 > 標頭。

|||
|-|-|
|`operator==`|測試運算子左邊的 URNG 是否等於右邊的引擎。|
|`operator!=`|測試運算子左邊的 URNG 是否不等於右邊的引擎。|
|`operator<<`|將狀態資訊寫入資料流。|
|`operator>>`|從資料流中擷取狀態資訊。|

## <a name="engdist"></a> 引擎和分佈

以下幾節，如每個範本類別分類中定義的詳細資訊，請參閱\<隨機 >。 這兩個範本類別分類採用類型做為引數，並使用共用範本參數名稱，以描述允許做為實際引數類型的類型屬性，如下所示：

- `IntType` 指出 `short`、`int`、`long`、`long long`、`unsigned short`、`unsigned int`、`unsigned long` 或 `unsigned long long`。

- `UIntType` 指出 `unsigned short`、`unsigned int`、`unsigned long` 或 `unsigned long long`。

- `RealType` 指出 `float`、`double` 或 `long double`。

### <a name="engines"></a>引擎

[引擎範本](#eng)和[引擎配接器範本](#engadapt)是其參數會自訂所建立之產生器的範本。

「引擎」是一種類別或樣板類別，其執行個體 (產生器) 做為統一分佈在最小值與最大值之間的亂數來源。 「引擎配接器」會採用部分其他亂數引擎所產生的值，並將某種類型的演算法套用至那些值，以傳遞一連串具有不同隨機性屬性的值。

每個引擎和引擎配接器都具有下列成員：

- `typedef` `numeric-type` `result_type` 是產生器 `operator()` 傳回的類型。 在具現化時，會將 `numeric-type` 傳遞為範本參數。

- `result_type operator()` 會傳回統一分佈在 `min()` 與 `max()` 之間的值。

- `result_type min()` 會傳回產生器的 `operator()` 所傳回的最小值。 引擎配接器會使用基底引擎的 `min()` 結果。

- `result_type max()` 會傳回產生器的 `operator()` 所傳回的最大值。 `result_type` 是整數 (整數值) 類型時，`max()` 是可以實際傳回的最大值 (內含)；`result_type` 是浮點 (實數值) 類型時，`max()` 是大於可傳回之所有值的最小值 (非內含)。 引擎配接器會使用基底引擎的 `max()` 結果。

- `void seed(result_type s)` 會使用種子值 `s` 植入產生器。 針對引擎，預設參數支援的簽章是 `void seed(result_type s = default_seed)` (引擎配接器會定義個別 `void seed()`，請參閱下一個小節)。

- `template <class Seq> void seed(Seq& q)` 會使用 [seed_seq](../standard-library/seed-seq-class.md)`Seq` 植入產生器。

- 具有引數 `result_type x` 的明確建構函式，會建立植入的產生器，就像藉由呼叫 `seed(x)` 一樣。

- 具有引數 `seed_seq& seq` 的明確建構函式，會建立植入的產生器，就像藉由呼叫 `seed(seq)` 一樣。

- `void discard(unsigned long long count)` 會有效率地呼叫 `operator()` `count` 次，並捨棄每個值。

**引擎配接器**額外支援這些成員 (`Engine` 是引擎配接器的第一個範本參數，會指定基底引擎類型)：

- 初始化產生器的預設建構函式，就像來自基底引擎的預設建構函式一樣。

- 引數為 `const Engine& eng` 的明確建構函式。 這是使用基底引擎來支援複製建構函式。

- 引數為 `Engine&& eng` 的明確建構函式。 這是使用基底引擎來支援移動建構函式。

- 使用基底引擎預設種子值來初始化產生器的 `void seed()`。

- 傳回用於建構產生器之基底引擎的 `const Engine& base()` 屬性函式。

每個引擎都會維護一個「狀態」，而狀態會決定後續呼叫 `operator()` 所產生的值序列。 使用 `operator==` 和 `operator!=`，可以比較從相同類型的引擎具現化的兩個產生器的狀態。 如果兩種狀態比較為相等，則會產生相同的值序列。 使用產生器的 `operator<<`，可以將物件的狀態儲存至資料流，且形式為一連串 32 位元不帶正負號值。 狀態在儲存之後並不會變更。 使用 `operator>>`，可以將儲存的狀態讀取至從相同類型的引擎具現化的產生器。

### <a name="distributions"></a>分佈

[「隨機亂數分佈」](#distributions)是一種類別或樣板類別，其執行個體會將取自引擎之統一分佈亂數的資料流，轉換為具有特定分佈之亂數的資料流。 每個分佈都有下列成員：

- `typedef` `numeric-type` `result_type` 是分佈的 `operator()` 所傳回的類型。 在具現化時，會將 `numeric-type` 傳遞為範本參數。

- `template <class URNG> result_type operator()(URNG& gen)` 會傳回根據分佈定義所分佈的值，方法是使用 `gen` 做為統一分佈隨機值的來源，以及儲存之「分佈的參數」。

- `template <class URNG> result_type operator()(URNG& gen, param_type p)` 會傳回按照分佈定義所分佈的值，方法是使用 `gen` 做為統一分佈隨機值的來源，以及參數結構 `p`。

- `typedef` `unspecified-type` `param_type` 是選擇性地傳遞至 `operator()` 的參數封裝，以及用來取代儲存的參數以產生其傳回值。

- `const param&` 建構函式會從其引數初始化儲存的參數。

- `param_type param() const` 取得儲存的參數。

- `void param(const param_type&)` 會從其引數設定儲存的參數。

- `result_type min()` 會傳回分佈的 `operator()` 所傳回的最小值。

- `result_type max()` 會傳回分佈的 `operator()` 所傳回的最大值。 `result_type` 是整數 (整數值) 類型時，`max()` 是可以實際傳回的最大值 (內含)；`result_type` 是浮點 (實數值) 類型時，`max()` 是大於可傳回之所有值的最小值 (非內含)。

- `void reset()` 會捨棄任何快取的值，讓下個 `operator()` 呼叫的結果不是取決於呼叫之前取自引擎的任何值。

參數結構是一個物件，其中儲存分佈所需的所有參數。 它包含：

- `typedef` `distribution-type` `distribution_type`，這是其分佈的類型。

- 一個或多個建構函式，採用與分佈建構函式所採用的相同參數清單。

- 與分佈相同的參數存取函式。

- 等號和不等比較運算子。

如需詳細資訊，請參閱本文之前的連結中，本主題下面的參考副主題。

## <a name="comments"></a> 備註

在 Visual Studio 中，有兩個極為有用的 URNG (`mt19937` 和 `random_device`)，如此比較表所示：

|URNG|快速|具有加密保護|可植入|具決定性|
|----------|-----------|---------------------|---------------|--------------------|
|`mt19937`|[是]|否|[是]|是<sup>*</sup>|
|`random_device`|否|是|否|否|

<sup>* 提供已知種子時。</sup>

雖然 ISO C++ 標準不需要加密保護 `random_device`，但在 Visual Studio 中，會將它實作為進行加密保護。 「加密保護」這個詞彙並不表示提供保證，而是指給定隨機演算法所提供的最低熵層級 (因此是預測層級)。 如需詳細資訊，請參閱 Wikipedia 文章：[密碼學安全偽亂數生成器](http://go.microsoft.com/fwlink/p/?linkid=398017)。因為 ISO C++ 標準不需要這個，所以其他平台可能會將 `random_device` 實作為簡單虛擬亂數產生器 (未加密保護)，而且可能只適合做為另一個產生器的種子來源。 在跨平台程式碼中使用 `random_device` 時，請參閱哪些平台的文件。

透過定義，`random_device` 結果是無法重新產生的，而且副作用是執行速度會明顯比其他 URNG 慢。 雖然您可能想要使用 `random_device` 呼叫來進行植入 (如[程式碼範例](#code)中所示)，但大部分不需要加密保護的應用程式都會使用 `mt19937` 或類似的引擎。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
