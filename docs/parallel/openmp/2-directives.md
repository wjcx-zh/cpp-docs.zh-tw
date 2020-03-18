---
title: 2. 指示詞
ms.date: 01/18/2019
ms.assetid: d1a69374-6c03-45fb-8c86-e91cea8adae8
ms.openlocfilehash: 125d2d83b277e62d007e3a208e426ea717d52790
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417086"
---
# <a name="2-directives"></a>2. 指示詞

指示詞是以 C 和C++標準中定義的 `#pragma` 指示詞為基礎。  支援 OpenMP C 和C++ API 的編譯器會包含命令列選項，它會啟動並允許解讀所有 OpenMP 編譯器指示詞。

## <a name="21-directive-format"></a>2.1 指示詞格式

OpenMP 指示詞的語法是由[附錄 C](c-openmp-c-and-cpp-grammar.md)中的文法正式指定，非正式的方式如下：

```cpp
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

每個指示詞的開頭都是 `#pragma omp`，以降低與其他（非 OpenMP 或供應商延伸至 OpenMP）相同名稱的 pragma 指示詞衝突的可能性。 指示詞的其餘部分會遵循編譯器指示詞之 C C++和標準的慣例。 特別的是，可以在 `#`之前和之後使用空白字元，有時必須使用空白字元來分隔指示詞中的單字。 遵循 `#pragma omp` 的前置處理權杖會受到宏取代。

指示詞會區分大小寫。 子句出現在指示詞中的順序並不重要。 指示詞 on 指示詞可能會視需要重複，受限於每個子句的描述中所列的限制。 如果*變數清單*出現在子句中，它必須僅指定變數。 每個指示詞只可指定一個指示詞*名稱*。  例如，不允許使用下列指示詞：

```cpp
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

OpenMP 指示詞最多隻適用于一個成功的語句，這必須是結構化的區塊。

## <a name="22-conditional-compilation"></a>2.2 條件式編譯

`_OPENMP` 宏名稱是由 OpenMP 相容的實作為 decimal 常數*yyyymm*所定義，這會是核准規格的年份和月份。 這個宏不得為 `#define` 或 `#undef` 前置處理指示詞的主體。

```cpp
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

如果廠商定義 OpenMP 的延伸模組，則可以指定其他預先定義的宏。

## <a name="23-parallel-construct"></a>2.3 平行結構

下列指示詞會定義平列區域，這是多個執行緒平行執行之程式的區域。 這個指示詞是啟動平行執行的基礎結構。

```cpp
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block
```

*子句*為下列其中一項：

- `if(` 純量*運算式*`)`
- `private(`*變數清單*`)`
- `firstprivate(`*變數清單*`)`
- `default(shared | none)`
- `shared(`*變數清單*`)`
- `copyin(`*變數清單*`)`
- `reduction(`*運算子*`:`*變數清單*`)`
- `num_threads(`*整數運算式*`)`

當執行緒到達平行結構時，如果下列其中一種情況成立，就會建立執行緒的小組：

- 沒有 `if` 子句。
- `if` 運算式會評估為非零值。

這個執行緒會成為小組的主要執行緒，其執行緒數目為0，而小組中的所有線程（包括主要執行緒）會以平行方式執列區域。 如果 `if` 運算式的值為零，則會序列化區域。

為了判斷所要求的執行緒數目，將依序考慮下列規則。 會套用符合條件的第一個規則：

1. 如果 `num_threads` 子句存在，則整數運算式的值會是所要求的執行緒數目。

1. 如果已呼叫 `omp_set_num_threads` 程式庫函式，則最近執行之呼叫中的引數值會是所要求的執行緒數目。

1. 如果環境變數 `OMP_NUM_THREADS` 已定義，則此環境變數的值會是所要求的執行緒數目。

1. 如果未使用上述的任何方法，則要求的執行緒數目為「執行定義」。

如果 `num_threads` 子句存在，則它會取代 `omp_set_num_threads` 程式庫函式所要求的執行緒數目，或僅針對其套用的平列區域使用 `OMP_NUM_THREADS` 環境變數。 較新的平列區域不受其影響。

執行平列區域的執行緒數目也取決於是否已啟用執行緒數目的動態調整。 如果動態調整已停用，則要求的執行緒數目將會執行平列區域。 如果啟用動態調整，則要求的執行緒數目就是可能執行平列區域的執行緒數目上限。

如果在停用執行緒數目的動態調整時遇到平列區域，而且針對平列區域要求的執行緒數目大於執行時間系統可以提供的數目，則程式的行為是執行定義。 例如，可能會中斷程式的執行，或者可能會序列化平列區域。

`omp_set_dynamic` 程式庫函式和 `OMP_DYNAMIC` 環境變數可以用來啟用和停用執行緒數目的動態調整。

在任何指定時間實際裝載執行緒的實體處理器數目，都是實作為定義的。 建立之後，小組中的執行緒數目在該平列區域的持續時間內會保持不變。 它可以由使用者明確地變更，或由執行時間系統自動由一個平列區域變更為另一個。

包含在平列區域動態範圍內的語句會由每個執行緒執行，而且每個執行緒都可以執行與其他執行緒不同的語句路徑。 在平列區域的詞法範圍外遇到的指示詞稱為孤立的指示詞。

在平列區域的結尾有隱含的屏障。 只有小組的主要執行緒會在平列區域結束時繼續執行。

如果小組中執行平列區域的執行緒遇到另一個平行結構，它會建立新的小組，而且它會成為該新小組的主要複本。 預設會序列化嵌套的平列區域。 因此，依預設，由一個執行緒組成的小組會執行一個嵌套的平列區域。 您可以使用執行時間程式庫函數 `omp_set_nested` 或環境變數 `OMP_NESTED`來變更預設行為。 不過，小組中執行嵌套平列區域的執行緒數目是實作為定義的。

`parallel` 指示詞的限制如下：

- 最多隻能有一個 `if` 子句出現在指示詞上。

- 不論 if 運算式或 `num_threads` 運算式內是否有任何副作用，都不會指定。

- 在平列區域內執行的 `throw` 必須導致在相同結構化區塊的動態範圍內繼續執行，而且它必須由擲回例外狀況的同一個執行緒捕捉。

- 指示詞上只能出現一個 `num_threads` 子句。 `num_threads` 運算式會在平列區域的內容之外進行評估，而且必須評估為正整數值。

- 未指定 `if` 和 `num_threads` 子句的評估順序。

### <a name="cross-references"></a>交互參考

- `private`、`firstprivate`、`default`、`shared`、`copyin`和 `reduction` 子句（[區段 2.7.2](#272-data-sharing-attribute-clauses)）
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)環境變數
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)程式庫函式
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)環境變數
- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function)函式
- [OMP_NESTED](4-environment-variables.md#44-omp_nested)環境變數
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function)程式庫函式

## <a name="24-work-sharing-constructs"></a>2.4 工作共用結構

工作共用結構會將相關聯語句的執行散發到遇到此專案之小組的成員之間。 工作共用指示詞不會啟動新的執行緒，而且在進入工作共用結構時，不會有隱含的屏障。

小組中的每個執行緒所遇到的工作共用結構和 `barrier` 指示詞的順序必須相同。

OpenMP 會定義下列工作共用結構，而下列各節將說明這些結構：

- [for](#241-for-construct)指示詞
- [sections](#242-sections-construct)指示詞
- [單一](#243-single-construct)指示詞

### <a name="241-for-construct"></a>2.4.1 for 結構

`for` 指示詞會識別反復的工作共用結構，指定相關聯迴圈的反覆運算將會平行執行。 `for` 迴圈的反復專案會散發到小組中已存在於執行其所系結之平行結構的執行緒。 `for` 結構的語法如下所示：

```cpp
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

子句為下列其中一項：

- `private(`*變數清單*`)`
- `firstprivate(`*變數清單*`)`
- `lastprivate(`*變數清單*`)`
- `reduction(`*運算子*`:`*變數清單*`)`
- `ordered`
- `schedule(`*種類*[`,` *chunk_size*] `)`
- `nowait`

`for` 指示詞會對對應 `for` 迴圈的結構施加限制。 具體而言，對應的 `for` 迴圈必須具有標準圖形：

`for (` *init-expr* `;` *var 邏輯 op b* `;`*增量-expr* `)`

*init-expr*<br/>
發生下列情形之一：

- *var* = *lb*
- *整數類型的 var* = *lb*

*增量-expr*<br/>
發生下列情形之一：

- `++` *var*
- *var* `++`
- `--` *var*
- *var* `--`
- *var* `+=`*增量*
- *var* `-=`*增量*
- *var* `=` *var* `+`*增量*
- *var* `=`*增量*`+` *var*
- *var* `=` *var* `-`*增量*

*var*<br/>
帶正負號的整數變數。 如果要共用此變數，則會在 `for`期間以隱含方式將它設為私用。 請勿在 `for` 語句的主體中修改此變數。 除非 `lastprivate`指定變數，否則在迴圈之後的值為不定。

*邏輯 op*<br/>
發生下列情形之一：

- `<`
- `<=`
- `>`
- `>=`

*lb*、 *b*和*增量*<br>
迴圈不變的整數運算式。 評估這些運算式時，不會進行同步處理，因此任何評估的副作用都會產生不確定的結果。

標準格式可讓迴圈反覆運算的數目在進入迴圈時計算。 這項計算是以*var*類型的值，在整數提升後進行。 特別是，如果*b*的值 `-` *lb* `+`*增量*無法在該類型中表示，則結果會是不確定的。 此外，如果*邏輯 op* `<` 或 `<=`，則*增量-expr*在迴圈的每個反覆運算上都必須造成*var*增加。   如果 `>` 或 `>=`*邏輯 op* ，則在迴圈的每次反覆運算時，*增量-expr*必須使*var*變得較小。

`schedule` 子句會指定如何將 `for` 迴圈的反復專案分割成小組的各個執行緒。 程式的正確性不能取決於執行特定反復專案的執行緒。 如有指定， *chunk_size*的值必須是具有正值的迴圈不變整數運算式。 評估此運算式時，不會進行同步處理，因此任何評估的副作用都會產生不確定的結果。 排程*種類*可以是下列其中一個值：

資料表2-1： `schedule` 子句*種類*值

|||
|-|-|
|靜態|指定 `schedule(static,` *chunk_size* `)` 時，反復專案會分割為*chunk_size*所指定大小的區塊。 區塊會以迴圈配置資源方式，以執行緒數目的順序，以靜態方式指派給小組中的執行緒。 當未指定任何*chunk_size*時，反復專案空間會分成大約大小相等的區塊，並將一個區塊指派給每個執行緒。|
|動態|指定 `schedule(dynamic,` *chunk_size* `)` 時，反復專案會分割成一連串的區塊，每個區塊都包含*chunk_size*的反復專案。 每個區塊都會指派給等待指派的執行緒。 執行緒會執行反復專案的區塊，然後等候其下一個指派，直到沒有任何區塊被指派為止。 要指派的最後一個區塊可能會有較少的反復專案數目。 若未指定*chunk_size* ，預設值為1。|
|指導|指定 `schedule(guided,` *chunk_size* `)` 時，反復專案會以減少的大小，指派給區塊中的執行緒。 當執行緒完成其指派的反復專案區塊時，它會以動態方式指派另一個區塊，直到沒有剩餘的為止。 對於1的*chunk_size* ，每個區塊的大小大約是未指派的反復專案數除以執行緒數目。 這些大小幾乎會以指數方式減少為1。 若為值為*k*大於1的*chunk_size* ，則大小幾乎會以指數方式減少為*k*，不同之處在于最後一個區塊的反覆運算可能少於*k*個。 若未指定*chunk_size* ，預設值為1。|
|執行階段|當指定 `schedule(runtime)` 時，有關排程的決策會延遲到執行時間為止。 您可以藉由設定環境變數 `OMP_SCHEDULE`，在執行時間選擇區塊的排程*種類*和大小。 如果未設定此環境變數，則產生的排程為「執行定義」。 當指定 `schedule(runtime)` 時，就不能指定*chunk_size* 。|

如果沒有明確定義的 `schedule` 子句，預設 `schedule` 為「執行定義」。

OpenMP 相容的程式不應依賴特定排程來執行正確的工作。 程式不應依賴符合上述描述的排程*種類*，因為在不同的編譯器中，可能會有相同排程*種類*的執行變化。 描述可用來選取適用于特定情況的排程。

當 `ordered` 指示詞系結至 `for` 結構時，必須要有 `ordered` 子句。

除非指定了 `nowait` 子句，否則 `for` 結構的結尾會有隱含的屏障。

`for` 指示詞的限制如下：

- `for` 迴圈必須是結構化區塊，此外，它的執行不得由 `break` 語句終止。

- 與 `for` 指示詞相關聯之 `for` 迴圈的迴圈控制運算式的值，對於小組中的所有線程都必須相同。

- `for` 迴圈反覆運算變數必須有帶正負號的整數類型。

- `for` 指示詞上只能出現一個 `schedule` 子句。

- `for` 指示詞上只能出現一個 `ordered` 子句。

- `for` 指示詞上只能出現一個 `nowait` 子句。

- 如果*chunk_size*、 *lb*、 *b*或*增量*運算式中發生任何副作用，就不會指定它。

- 小組中所有線程的*chunk_size*運算式的值都必須相同。

#### <a name="cross-references"></a>交互參考

- `private`、`firstprivate`、`lastprivate`和 `reduction` 子句（[區段 2.7.2](#272-data-sharing-attribute-clauses)）
- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule)環境變數
- 已[排序](#266-ordered-construct)的結構
- [schedule](d-using-the-schedule-clause.md)子句

### <a name="242-sections-construct"></a>2.4.2 區段結構

`sections` 指示詞會識別 noniterative 的工作共用結構，其指定要在小組中的執行緒之間劃分的一組結構。 每個區段都會由小組中的執行緒執行一次。 `sections` 指示詞的語法如下所示：

```cpp
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

子句為下列其中一項：

- `private(`*變數清單*`)`
- `firstprivate(`*變數清單*`)`
- `lastprivate(`*變數清單*`)`
- `reduction(`*運算子*`:`*變數清單*`)`
- `nowait`

雖然第一個區段的 `section` 指示詞是選擇性的，但每個區段的前面都會加上 `section` 指示詞。 `section` 指示詞必須出現在 `sections` 指示詞的詞法範圍內。 除非指定 `nowait`，否則 `sections` 結構的結尾會有隱含的屏障。

`sections` 指示詞的限制如下：

- `section` 指示詞不能出現在 `sections` 指示詞的詞法範圍外。

- `sections` 指示詞上只能出現一個 `nowait` 子句。

#### <a name="cross-references"></a>交互參考

- `private`、`firstprivate`、`lastprivate`和 `reduction` 子句（[區段 2.7.2](#272-data-sharing-attribute-clauses)）

### <a name="243-single-construct"></a>2.4.3 單一結構

`single` 指示詞會識別結構，指定相關聯的結構化區塊僅由小組中的一個執行緒執行（不一定是主要執行緒）。 `single` 指示詞的語法如下所示：

```cpp
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

子句為下列其中一項：

- `private(`*變數清單*`)`
- `firstprivate(`*變數清單*`)`
- `copyprivate(`*變數清單*`)`
- `nowait`

除非指定了 `nowait` 子句，否則 `single` 結構之後會有隱含的屏障。

`single` 指示詞的限制如下：

- `single` 指示詞上只能出現一個 `nowait` 子句。
- `copyprivate` 子句不得與 `nowait` 子句一起使用。

#### <a name="cross-references"></a>交互參考

- `private`、`firstprivate`和 `copyprivate` 子句（[區段 2.7.2](#272-data-sharing-attribute-clauses)）

## <a name="25-combined-parallel-work-sharing-constructs"></a>2.5 結合的平行工作共用結構

結合的平行工作共用結構是用來指定僅有一個工作共用結構之平列區域的快捷方式。 這些指示詞的語義與明確指定 `parallel` 指示詞，後面接著單一工作共用結構相同。

下列各節說明結合的平行工作共用結構：

- [parallel for](#251-parallel-for-construct)指示詞
- [parallel sections](#252-parallel-sections-construct)指示詞

### <a name="251-parallel-for-construct"></a>2.5.1 parallel for 結構

`parallel for` 指示詞是 `parallel` 區域的快捷方式，其中只包含單一的 `for` 指示詞。 `parallel for` 指示詞的語法如下所示：

```cpp
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

這個指示詞允許 `parallel` 指示詞和 `for` 指示詞的所有子句，但 `nowait` 子句除外，其意義和限制相同。 此語義與明確指定緊接在 `for` 指示詞後面的 `parallel` 指示詞相同。

#### <a name="cross-references"></a>交互參考

- [parallel](#23-parallel-construct)指示詞
- [for](#241-for-construct)指示詞
- [資料屬性子句](#272-data-sharing-attribute-clauses)

### <a name="252-parallel-sections-construct"></a>2.5.2 平行區段結構

`parallel sections` 指示詞會提供快捷方式表單，用來指定只有單一 `sections` 指示詞的 `parallel` 區域。 此語義與明確指定緊接在 `sections` 指示詞後面的 `parallel` 指示詞相同。 `parallel sections` 指示詞的語法如下所示：

```cpp
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

*子句*可以是 `parallel` 和 `sections` 指示詞所接受的其中一個子句，但不包括 `nowait` 子句。

#### <a name="cross-references"></a>交互參考

- [parallel](#23-parallel-construct)指示詞
- [sections](#242-sections-construct)指示詞

## <a name="26-master-and-synchronization-directives"></a>2.6 主要和同步處理指示詞

下列各節說明：

- [主要](#261-master-construct)結構
- [重大](#262-critical-construct)結構
- [屏障](#263-barrier-directive)指示詞
- 不可部分完成[的結構](#264-atomic-construct)
- [flush](#265-flush-directive)指示詞
- 已[排序](#266-ordered-construct)的結構

### <a name="261-master-construct"></a>2.6.1 主要結構

`master` 指示詞會識別指定由小組的主要執行緒執行之結構化區塊的結構。 `master` 指示詞的語法如下所示：

```cpp
#pragma omp master new-linestructured-block
```

小組中的其他執行緒不會執行相關聯的結構化區塊。 在進入或離開主要結構時，不會有隱含的屏障。

### <a name="262-critical-construct"></a>2.6.2 關鍵結構

`critical` 指示詞會識別一次將相關聯結構區塊的執行限制為單一線程的結構。 `critical` 指示詞的語法如下所示：

```cpp
#pragma omp critical [(name)]  new-linestructured-block
```

選擇性的*名稱*可用來識別重要區域。 用來識別重要區域的識別碼具有外部連結，而且位於與標籤、標記、成員和一般識別碼所使用之命名空間不同的命名空間中。

執行緒會在關鍵區域的開頭等待，直到沒有其他執行緒執行具有相同名稱的重要區域（在程式中的任何位置）為止。 所有未命名的 `critical` 指示詞都會對應到相同的未指定名稱。

### <a name="263-barrier-directive"></a>2.6.3 屏障指示詞

`barrier` 指示詞會同步處理小組中的所有線程。 遇到時，小組中的每個執行緒都會等待，直到所有人都達到此點為止。 `barrier` 指示詞的語法如下所示：

```cpp
#pragma omp barrier new-line
```

在小組中的所有線程都遇到屏障之後，小組中的每個執行緒都會開始以平行方式在關卡指示詞之後執行語句。 由於 `barrier` 指示詞沒有 C 語言語句作為其語法的一部分，因此在程式內的位置會有一些限制。 如需有關正式文法的詳細資訊，請參閱[附錄 C](c-openmp-c-and-cpp-grammar.md)。下列範例說明這些限制。

```cpp
/* ERROR - The barrier directive cannot be the immediate
*          substatement of an if statement
*/
if (x!=0)
   #pragma omp barrier
...

/* OK - The barrier directive is enclosed in a
*      compound statement.
*/
if (x!=0) {
   #pragma omp barrier
}
```

### <a name="264-atomic-construct"></a>2.6.4 不可部分完成的結構

`atomic` 指示詞可確保特定記憶體位置會以自動方式更新，而不會公開給多個同時寫入執行緒的可能性。 `atomic` 指示詞的語法如下所示：

```cpp
#pragma omp atomic new-lineexpression-stmt
```

運算式語句必須具有下列其中一種形式：

- *x binop* `=` *expr*
- *x* `++`
- `++` *x*
- *x* `--`
- `--` *x*

在上述運算式中：

- *x*是具有純量類型的左值運算式。

- *expr*是具有純量類型的運算式，而且不會參考*x*所指定的物件。

- *binop*不是多載運算子，而且是 `+`、`*`、`-`、`/`、`&`、`^`、`|`、`<<`或 `>>`的其中一個。

雖然它是實作為定義的，但執行會將所有 `atomic` 指示詞取代為具有相同唯一*名稱*`critical` 指示詞，但 `atomic` 指示詞允許更佳的優化。 通常可以使用硬體指示，以最少的額外負荷來執行不可部分完成的更新。

只有*x*所指定之物件的載入和存放是不可部分完成的;*expr*的評估不是不可部分完成的。 為避免競爭情況，所有平行位置的更新都應該使用 `atomic` 指示詞來保護，但已知不會有競爭情況的例外狀況。

`atomic` 指示詞的限制如下：

- 整個程式中儲存位置 x 的所有不可部分完成參考都必須要有相容的類型。

#### <a name="examples"></a>範例

```cpp
extern float a[], *p = a, b;
/* Protect against races among multiple updates. */
#pragma omp atomic
a[index[i]] += b;
/* Protect against races with updates through a. */
#pragma omp atomic
p[i] -= 1.0f;

extern union {int n; float x;} u;
/* ERROR - References through incompatible types. */
#pragma omp atomic
u.n++;
#pragma omp atomic
u.x -= 1.0f;
```

### <a name="265-flush-directive"></a>2.6.5 flush 指示詞

`flush` 指示詞（不論是明確或隱含）會指定需要執行的「跨執行緒」序列點，以確保小組中的所有線程都在記憶體中具有特定物件（如下所指定）的一致觀點。 這表示先前參考這些物件之運算式的評估已完成，且後續的評估尚未開始。 例如，編譯器必須從暫存器將物件的值還原至記憶體，而硬體可能需要將寫入緩衝區排清至記憶體，並從記憶體重載物件的值。

`flush` 指示詞的語法如下所示：

```cpp
#pragma omp flush [(variable-list)]  new-line
```

如果需要同步處理的物件都可以透過變數來指定，則可以在選擇性的*變數清單*中指定這些變數。 如果指標存在於*變數清單*中，指標本身會排清，而不是指標所參考的物件。

沒有*變數清單*的 `flush` 指示詞會同步處理所有共用物件，但具有自動儲存期的無法存取物件除外。 （這可能會造成額外負荷，而不是具有*變數清單*的 `flush`）。不含*變數清單*的 `flush` 指示詞，會隱含用於下列指示詞：

- `barrier`
- 進入或離開 `critical`
- 進入或離開 `ordered`
- 進入或離開 `parallel`
- 離開時 `for`
- 離開時 `sections`
- 離開時 `single`
- 進入或離開 `parallel for`
- 進入或離開 `parallel sections`

如果有 `nowait` 子句，則不隱含指示詞。 請注意，`flush` 指示詞不會隱含為下列任何一項：

- 進入 `for`
- 進入或離開 `master`
- 進入 `sections`
- 進入 `single`

存取具有變動性限定類型之物件值的參考，如同在上一個序列點上指定該物件的 `flush` 指示詞一樣。 使用變動性限定類型來修改物件值的參考，如同在後續序列點上指定該物件的 `flush` 指示詞一樣。

由於 `flush` 指示詞沒有 C 語言語句作為其語法的一部分，因此在程式內的位置會有一些限制。 如需有關正式文法的詳細資訊，請參閱[附錄 C](c-openmp-c-and-cpp-grammar.md)。下列範例說明這些限制。

```cpp
/* ERROR - The flush directive cannot be the immediate
*          substatement of an if statement.
*/
if (x!=0)
   #pragma omp flush (x)
...

/* OK - The flush directive is enclosed in a
*      compound statement
*/
if (x!=0) {
   #pragma omp flush (x)
}
```

`flush` 指示詞的限制如下：

- 在 `flush` 指示詞中指定的變數不能有參考型別。

### <a name="266-ordered-construct"></a>2.6.6 已排序的結構

遵循 `ordered` 指示詞之後的結構化區塊，會依照在連續迴圈中執行反覆運算的循序執行。 `ordered` 指示詞的語法如下所示：

```cpp
#pragma omp ordered new-linestructured-block
```

`ordered` 指示詞必須在 `for` 或 `parallel for` 結構的動態範圍內。 `ordered` 結構系結的 `for` 或 `parallel for` 指示詞必須指定 `ordered` 子句，如[2.4.1 一節](#241-for-construct)中所述。 在使用 `ordered` 子句執行 `for` 或 `parallel for` 結構時，`ordered` 的結構會嚴格地以執行迴圈時的循序執行。

`ordered` 指示詞的限制如下：

- 具有 `for` 結構之迴圈的反復專案，不能多次執行相同的已排序指示詞，而且它不能執行一個以上的 `ordered` 指令詞。

## <a name="27-data-environment"></a>2.7 資料環境

本節提供指示詞和數個子句，以便在平列區域執行期間控制資料環境，如下所示：

- 提供[threadprivate](#271-threadprivate-directive)指示詞，讓檔案範圍、命名空間範圍或靜態區塊範圍變數成為執行緒的本機。

- [2.7.2 一節](#272-data-sharing-attribute-clauses)中會說明可在指示詞上指定的子句，以控制平行或工作共用結構期間變數的共用屬性。

### <a name="271-threadprivate-directive"></a>2.7.1 threadprivate 指示詞

`threadprivate` 指示詞會將名為的檔案範圍、命名空間範圍或靜態區塊範圍變數指定于執行緒的私用*變數清單*中。 *變數清單*是以逗號分隔的變數清單，其中沒有不完整的類型。 `threadprivate` 指示詞的語法如下所示：

```cpp
#pragma omp threadprivate(variable-list) new-line
```

`threadprivate` 變數的每個複本會在第一次參考該複本之前，于程式中未指定的點初始化一次，並以一般方式（也就是，因為主要複本會在程式的序列執行中初始化）。 請注意，如果在 `threadprivate` 變數的明確初始化運算式中參考物件，而且在第一次參考該變數之前修改物件的值，則會未指定行為。

如同任何私用變數，執行緒不能參考另一個執行緒的 `threadprivate` 物件複本。 在程式的序欄區域和主要區域中，參考會指向物件的主要執行緒複本。

第一個平列區域執行之後，只有在已停用動態執行緒機制，而且所有平列區域的執行緒數目保持不變時，才會保證 `threadprivate` 物件中的資料會保存。

`threadprivate` 指示詞的限制如下：

- 檔案範圍或命名空間範圍變數的 `threadprivate` 指示詞必須出現在任何定義或宣告之外，而且必須以詞法的方式在其清單中任何變數的所有參考之前。

- 位於檔案或命名空間範圍之 `threadprivate` 指示詞的*變數清單*中的每個變數，都必須參考在述詞前面的檔案或命名空間範圍中的變數宣告。

- 靜態區塊範圍變數的 `threadprivate` 指示詞必須出現在變數的範圍中，而不是在嵌套的範圍中。 指示詞必須以詞法方式在其清單中任何變數的所有參考之前。

- 區塊範圍中 `threadprivate` 指示詞之*變數清單*中的每個變數，都必須參考在述詞前面的相同範圍中的變數宣告。 變數宣告必須使用 static 儲存類別規範。

- 如果變數是在一個轉譯單位的 `threadprivate` 指示詞中指定，則必須在其宣告所在的每個轉譯單位中，于 `threadprivate` 指示詞中指定。

- `threadprivate` 變數不能出現在 `copyin`、`copyprivate`、`schedule`、`num_threads`或 `if` 子句以外的任何子句中。

- `threadprivate` 變數的位址不是位址常數。

- `threadprivate` 變數不能有不完整的類型或參考型別。

- 具有非 POD 類別類型的 `threadprivate` 變數必須具有可存取且明確的複製程式，如果它是使用明確的初始化運算式來宣告。

下列範例說明如何修改出現在初始化運算式中的變數，可能會導致未指定的行為，以及如何使用輔助物件和複製-函數來避免這個問題。

```cpp
int x = 1;
T a(x);
const T b_aux(x); /* Capture value of x = 1 */
T b(b_aux);
#pragma omp threadprivate(a, b)

void f(int n) {
   x++;
   #pragma omp parallel for
   /* In each thread:
   * Object a is constructed from x (with value 1 or 2?)
   * Object b is copy-constructed from b_aux
   */
   for (int i=0; i<n; i++) {
      g(a, b); /* Value of a is unspecified. */
   }
}
```

#### <a name="cross-references"></a>交互參考

- [動態執行緒](3-run-time-library-functions.md#317-omp_set_dynamic-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)環境變數

### <a name="272-data-sharing-attribute-clauses"></a>2.7.2 資料共用屬性子句

有數個指示詞接受子句，可讓使用者在區域期間控制變數的共用屬性。 共用屬性子句僅適用于出現子句之指示詞的詞法範圍中的變數。 並非所有的指示詞都允許所有的下列子句。 在特定指示詞上有效的子句清單會與指示詞一起說明。

當遇到平行或工作共用結構時，如果變數是可見的，而且未在共用屬性子句或 `threadprivate` 指示詞中指定變數，則會共用該變數。 在平列區域的動態範圍內宣告的靜態變數會共用。 共用堆積配置的記憶體（例如，使用 C C++中的 `malloc()`，或中C++的 `new` 運算子）。 （不過，此記憶體的指標可以是私用或共用的）。在平列區域的動態範圍內宣告自動儲存持續時間的變數是私用的。

大部分的子句都會接受*可變清單*引數，這是可見的變數清單（以逗號分隔）。 如果資料共用屬性子句中參考的變數具有衍生自範本的類型，而且程式中沒有該變數的其他參考，則行為是未定義的。

出現在指示詞子句中的所有變數都必須是可見的。 子句可以視需要重複，但不能在多個子句中指定變數，不過，變數可以同時在 `firstprivate` 和 `lastprivate` 子句中指定。

下列各節描述資料共用屬性子句：

- [private](#2721-private)
- [firstprivate](#2722-firstprivate)
- [lastprivate](#2723-lastprivate)
- [共用](#2724-shared)
- [預設值](#2725-default)
- [reduction](#2726-reduction)
- [copyin](#2727-copyin)
- [copyprivate](#2728-copyprivate)

#### <a name="2721-private"></a>2.7.2.1 private

`private` 子句會將變數清單中的變數宣告為小組中每個執行緒的私用。 `private` 子句的語法如下所示：

```cpp
private(variable-list)
```

在 `private` 子句中指定之變數的行為如下所示。 會為結構配置具有自動儲存期的新物件。 新物件的大小和對齊取決於變數的類型。 這項配置會針對小組中的每個執行緒進行一次，並在必要時叫用 class 物件的預設函式;否則，初始值為不定。  變數所參考的原始物件在進入結構時具有不確定的值，不得在結構的動態範圍內修改，而且在從結構結束時具有不確定的值。

在指示詞結構的詞法範圍中，變數會輔助線程所配置的新私用物件。

`private` 子句的限制如下：

- 具有在 `private` 子句中指定之類別類型的變數，必須具有可存取、明確的預設函式。

- 在 `private` 子句中指定的變數不能有 `const`限定的類型，除非它具有具有 `mutable` 成員的類別類型。

- 在 `private` 子句中指定的變數不能有不完整的類型或參考型別。

- 在系結至平行結構之工作共用指示詞的 `private` 子句中，不能指定出現在 `parallel` 指示詞之 `reduction` 子句中的變數。

#### <a name="2722-firstprivate"></a>2.7.2.2 firstprivate

`firstprivate` 子句會提供 `private` 子句所提供的功能超集合。 `firstprivate` 子句的語法如下所示：

```cpp
firstprivate(variable-list)
```

*變數清單*中指定的變數具有 `private` 子句的語義，如[2.7.2.1 一節](#2721-private)中所述。 初始化或結構會像是線上程執行結構之前，在每個執行緒上執行一次。 若為平行結構上的 `firstprivate` 子句，新私用物件的初始值就是原始物件的值，該物件會在遇到該物件的執行緒平行結構之前立即存在。 針對工作共用結構上的 `firstprivate` 子句，執行工作共用結構之每個執行緒的新私用物件的初始值，是原始物件的值，在相同執行緒遇到工作共用結構的時間點之前存在。 此外，對於C++物件，每個執行緒的新私用物件會從原始物件進行複製。

`firstprivate` 子句的限制如下：

- 在 `firstprivate` 子句中指定的變數不能有不完整的類型或參考型別。

- 具有指定為 `firstprivate` 之類別類型的變數，必須具有可存取、明確的複製參數。

- 在平列區域內，或出現在 `parallel` 指示詞之 `reduction` 子句中的變數，不能指定于系結至平行結構之工作共用指示詞的 `firstprivate` 子句中。

#### <a name="2723-lastprivate"></a>2.7.2.3 lastprivate

`lastprivate` 子句會提供 `private` 子句所提供的功能超集合。 `lastprivate` 子句的語法如下所示：

```cpp
lastprivate(variable-list)
```

*變數清單*中指定的變數具有 `private` 子句的語義。 當 `lastprivate` 子句出現在識別工作共用結構的指示詞上時，每個 `lastprivate` 變數的值會從關聯的迴圈的最後一次反覆運算中，或在詞法上的最後一個區段指示詞中，指派給變數的原始物件。 `for` 或 `parallel for`的最後一個反覆運算或 `sections` 或 `parallel sections` 指示詞的最後一個區段中，未指定值的變數，在結構之後會有不確定的值。 未指派的子工作在結構之後也會有不確定的值。

`lastprivate` 子句的限制如下：

- 適用于 `private` 的所有限制。

- 具有指定為 `lastprivate` 之類別類型的變數，必須具有可存取、明確的複製指派運算子。

- 在平列區域內，或出現在 `parallel` 指示詞之 `reduction` 子句中的變數，不能指定于系結至平行結構之工作共用指示詞的 `lastprivate` 子句中。

#### <a name="2724-shared"></a>2.7.2.4 shared

這個子句會共用小組中所有線程之間出現在*變數清單*中的變數。 小組內的所有線程都會存取相同的儲存區域來 `shared` 變數。

`shared` 子句的語法如下所示：

```cpp
shared(variable-list)
```

#### <a name="2725-default"></a>2.7.2.5 default

`default` 子句可讓使用者影響變數的資料共用屬性。 `default` 子句的語法如下所示：

```cpp
default(shared | none)
```

指定 `default(shared)` 相當於在 `shared` 子句中明確列出每個可見的變數，除非它是 `threadprivate` 或 `const`限定的。 如果沒有明確的 `default` 子句，則預設行為會與指定 `default(shared)` 相同。

若要指定 `default(none)`，必須在平行結構的詞法範圍中，對變數的每個參考至少要有下列其中一項：

- 變數會明確列出在包含參考之結構的資料共用屬性子句中。

- 變數會在平行結構內宣告。

- 變數為 `threadprivate`。

- 變數具有 `const`限定的類型。

- 變數是 `for` 迴圈的迴圈控制變數，這會緊接在 `for` 或 `parallel for` 指示詞之後，而變數參考則會出現在迴圈內。

在封閉的指示詞的 `firstprivate`、`lastprivate`或 `reduction` 子句上指定變數，會導致在封入內容中隱含參考變數。 這類隱含參考也受限於上述需求。

`parallel` 指示詞上只能指定一個 `default` 子句。

您可以使用 `private`、`firstprivate`、`lastprivate`、`reduction`和 `shared` 子句來覆寫變數的預設資料共用屬性，如下列範例所示：

```cpp
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```

#### <a name="2726-reduction"></a>2.7.2.6 reduction

此子句會針對出現在*變數清單*中的純量變數，使用運算子*op*來減少其執行。 `reduction` 子句的語法如下所示：

`reduction(` *op* `:`*變數清單*`)`

對於具有下列其中一種形式的語句，通常會指定縮減：

- *x* `=` *x* *op* *運算式*
- *x* *binop* `=` *expr*
- *x* `=` *expr* *op* *x* （減法除外）
- *x* `++`
- `++` *x*
- *x* `--`
- `--` *x*

其中：

*x*<br/>
清單中指定的其中一個縮減變數。

*變數清單*<br/>
以逗號分隔的純量縮減變數清單。

*expr*<br/>
具有純量類型且未參考*x*的運算式。

*op*<br/>
不是多載運算子，而是其中一個 `+`、`*`、`-`、`&`、`^`、`|`、`&&`或 `||`。

*binop*<br/>
不是多載運算子，而是其中一個 `+`、`*`、`-`、`&`、`^`或 `|`。

以下是 `reduction` 子句的範例：

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

如範例所示，運算子可能會隱藏在函式呼叫內。 使用者應該小心，在 `reduction` 子句中指定的運算子符合減少作業。

雖然在此範例中，`||` 運算子的右運算元沒有副作用，但仍可加以使用，但應該小心使用。 在此情況下，在平行執行期間可能會發生迴圈不會發生的副作用。 這種差異可能是因為反覆運算的執行順序不確定。

運算子是用來判斷編譯器用來減少和判斷結束運算子的任何私用變數的初始值。 明確指定運算子可讓縮減語句超出結構的詞法範圍。 可以在指示詞上指定任意數目的 `reduction` 子句，但變數最多隻能出現在該指示詞的一個 `reduction` 子句中。

會針對每個執行緒建立一個*變數清單*中每個變數的私用複本，如同已使用 `private` 子句一樣。 私用複本會根據運算子進行初始化（請參閱下表）。

在指定 `reduction` 子句的區域結尾處，會更新原始物件，以反映將其原始值與每個私用複本的最終值結合的結果，並使用指定的運算子。 減少運算子全都是關聯的（減法除外），而編譯器可以自由地重新關聯最後值的計算。 （會加入減去縮減的部分結果，以形成最後的值）。

當第一個執行緒到達包含的子句時，原始物件的值會變成不定，而且會在縮減計算完成之前維持不變。  一般來說，計算會在結構的結尾完成;不過，如果 `reduction` 子句用於也套用 `nowait` 的結構，則原始物件的值會維持不變，直到執行屏障同步處理以確保所有線程都已完成 `reduction` 子句為止。

下表列出有效的運算子和其標準的初始化值。 實際的初始化值會與縮減變數的資料類型一致。

|運算子|初始化|
|--------------|--------------------|
|`+`|0|
|`*`|1|
|`-`|0|
|`&`|~0|
|`|`|0|
|`^`|0|
|`&&`|1|
|`||`|0|

`reduction` 子句的限制如下：

- `reduction` 子句中的變數類型必須對縮減運算子有效，不同之處在于不允許指標類型和參考型別。

- 在 `reduction` 子句中指定的變數不得 `const`限定。

- 在平列區域內，或出現在 `parallel` 指示詞之 `reduction` 子句中的變數，不能指定于系結至平行結構之工作共用指示詞的 `reduction` 子句中。

   ```cpp
   #pragma omp parallel private(y)
   { /* ERROR - private variable y cannot be specified
                in a reduction clause */
      #pragma omp for reduction(+: y)
      for (i=0; i<n; i++)
         y += b[i];
   }

   /* ERROR - variable x cannot be specified in both
              a shared and a reduction clause */
   #pragma omp parallel for shared(x) reduction(+: x)
   ```

#### <a name="2727-copyin"></a>2.7.2.7 copyin

`copyin` 子句會提供一個機制，為執行平列區域之小組中的每個執行緒，指派相同的值來 `threadprivate` 變數。 針對 `copyin` 子句中指定的每個變數，會將小組主要執行緒中的變數值複製到平列區域開頭的執行緒私用複本，如同指派一樣。 `copyin` 子句的語法如下所示：

```cpp

copyin(
variable-list
)
```

`copyin` 子句的限制如下：

- 在 `copyin` 子句中指定的變數必須具有可存取、明確的複製指派運算子。

- 在 `copyin` 子句中指定的變數必須是 `threadprivate` 變數。

#### <a name="2728-copyprivate"></a>2.7.2.8 copyprivate

`copyprivate` 子句提供一個機制，可使用私用變數，將一個小組成員的值廣播到其他成員。 當提供這類共用變數會很棘手（例如，在需要每個層級上有不同變數的遞迴中）時，就可以使用共用變數來取代值。 `copyprivate` 子句只能出現在 `single` 指示詞上。

`copyprivate` 子句的語法如下所示：

```cpp

copyprivate(
variable-list
)
```

在其變數清單中的變數上，`copyprivate` 子句的效果會在執行與 `single` 結構關聯的結構化區塊之後，以及在小組中的任何執行緒離開結構結尾的屏障之前發生。 然後，在小組的所有其他執行緒中，針對*變數清單*中的每個變數，會在執行結構結構化區塊的執行緒中，使用對應變數的值來定義變數（如同指派）。

`copyprivate` 子句的限制如下：

- 在 `copyprivate` 子句中指定的變數不能出現在相同 `single` 指示詞的 `private` 或 `firstprivate` 子句中。

- 如果在平列區域的動態範圍中遇到具有 `copyprivate` 子句的 `single` 指示詞，則在 `copyprivate` 子句中指定的所有變數在封入內容中都必須是私用的。

- 在 `copyprivate` 子句中指定的變數必須具有可存取的明確複製指派運算子。

## <a name="28-directive-binding"></a>2.8 指示詞系結

指示詞的動態繫結必須遵守下列規則：

- `for`、`sections`、`single`、`master`和 `barrier` 指示詞會系結至動態封閉 `parallel`（如果有的話），不論該指示詞上可能存在的任何 `if` 子句的值為何。 如果目前未執行任何平列區域，則指示詞是由只由主要執行緒組成的小組來執行。

- `ordered` 指示詞會系結至動態封閉 `for`。

- `atomic` 指示詞會對所有線程中的 `atomic` 指示詞強制執行獨佔存取權，而不只是針對目前的小組。

- `critical` 指示詞會對所有線程中的 `critical` 指示詞強制執行獨佔存取權，而不只是針對目前的小組。

- 指示詞絕不能系結到最接近的動態封入 `parallel`之外的任何指示詞。

## <a name="29-directive-nesting"></a>2.9 指示詞嵌套

指示詞的動態嵌套必須遵守下列規則：

- 在另一個 `parallel` 中動態 `parallel` 指示詞，會以邏輯方式建立新的小組，而這是由目前的執行緒所組成，除非已啟用嵌套平行處理原則。

- 系結至相同 `parallel` 的 `for`、`sections`和 `single` 指示詞不允許嵌套在彼此內部。

- 具有相同名稱的 `critical` 指示詞不允許嵌套在彼此內部。 請注意，這種限制不足以防止鎖死。

- 如果指示詞系結至與區域相同的 `ordered`，`critical`、`master` 和 `parallel` 區域的動態範圍中不允許 `for`、`sections`和 `single` 指示詞。

- 如果指示詞系結至與區域相同的 `single`，`for`、`ordered`、`sections`、`master`、`critical` 和 `parallel` 區域的動態範圍中不允許 `barrier` 指示詞。

- 如果 `master` 指示詞系結至與工作共用指示詞相同的 `parallel`，`for`、`sections`和 `single` 指示詞的動態範圍中不允許 `master` 指示詞。

- 如果指示詞系結至與區域相同的 `parallel`，`critical` 區域的動態範圍中不允許 `ordered` 指示詞。

- 當在平列區域外部執行時，也允許在平列區域內動態執行時所允許的任何指示詞。 以動態方式在使用者指定的平列區域外執行時，指示詞是由僅由主要執行緒組成的小組執行。
