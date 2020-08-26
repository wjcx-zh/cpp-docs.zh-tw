---
title: 2. 指示詞
ms.date: 01/18/2019
ms.assetid: d1a69374-6c03-45fb-8c86-e91cea8adae8
ms.openlocfilehash: 5b2649a65efd3368cf8a4d2649a424b1a539f1ef
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841970"
---
# <a name="2-directives"></a>2. 指示詞

指示詞是 `#pragma` 以 C 和 c + + 標準中定義的指示詞為基礎。  支援 OpenMP C 和 c + + API 的編譯器將包含命令列選項，可啟用並允許所有 OpenMP 編譯器指示詞的解讀。

## <a name="21-directive-format"></a>2.1 指示詞格式

OpenMP 指示詞的語法是由 [附錄 C](c-openmp-c-and-cpp-grammar.md)中的文法正式指定，且非正式方式如下：

```cpp
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

每個指示詞的開頭都  `#pragma omp` 是，以降低與其他 (非 openmp 或供應商延伸模組的衝突，以使 OpenMP) pragma 指示詞的名稱相同。 指示詞的其餘部分會遵循 C 和 c + + 標準的編譯器指示詞的慣例。 特別是，您可以在之前和之後使用空白字元 `#` ，有時必須使用空白字元來分隔指示詞中的單字。 後續的前置處理權杖 `#pragma omp` 會受到宏取代。

指示詞會區分大小寫。 子句出現在指示詞中的順序並不重要。 指示詞上的子句可能會視需要重複，受限於每個子句的描述中所列的限制。 如果 *變數清單* 出現在子句中，則必須只指定變數。 每個指示詞只可指定一個指示詞 *名稱* 。  例如，不允許下列指示詞：

```cpp
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

OpenMP 指示詞最多隻適用于一個後面的語句，這必須是結構化區塊。

## <a name="22-conditional-compilation"></a>2.2 條件式編譯

`_OPENMP`宏名稱是由 OpenMP 相容的實作為來定義，做為十進位常數*yyyymm*，它會是已核准規格的年份和月份。 此宏不得為或前置處理指示詞的主體 `#define` `#undef` 。

```cpp
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

如果廠商定義了 OpenMP 的延伸模組，則可以指定其他預先定義的宏。

## <a name="23-parallel-construct"></a>2.3 平行結構

下列指示詞會定義平列區域，這是由許多執行緒平行執行的程式區域。 這個指示詞是開始平行執行的基礎結構。

```cpp
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block
```

*子句*是下列其中一項：

- `if(`純量*運算式*`)`
- `private(`*變數清單*`)`
- `firstprivate(`*變數清單*`)`
- `default(shared | none)`
- `shared(`*變數清單*`)`
- `copyin(`*變數清單*`)`
- `reduction(`*運算子* `:`*變數清單*  `)`
- `num_threads(`*整數運算式*`)`

當執行緒到達平行結構時，如果下列其中一種情況成立，就會建立執行緒小組：

- 沒有 `if` 子句存在。
- `if`運算式評估為非零值。

此執行緒會成為小組的主要執行緒，執行緒編號為0，而小組中的所有線程（包括主要執行緒）會以平行方式執列區域。 如果運算式的值 `if` 為零，則會序列化區域。

為了判斷所要求的執行緒數目，會依序考慮下列規則。 第一個符合條件的規則將會套用：

1. 如果 `num_threads` 有子句，則整數運算式的值是要求的執行緒數目。

1. 如果 `omp_set_num_threads` 已呼叫程式庫函式，則最近執行的呼叫中的引數值就是要求的執行緒數目。

1. 如果已定義環境變數 `OMP_NUM_THREADS` ，則此環境變數的值為所要求的執行緒數目。

1. 如果未使用上述任何方法，則會要求執行的執行緒數目。

如果子句存在，則它會取代程式庫函式所 `num_threads` 要求的執行緒數目， `omp_set_num_threads` 或 `OMP_NUM_THREADS` 僅針對套用它的平列區域取代環境變數。 稍後的並列區域不會受到影響。

執行平列區域的執行緒數目也取決於是否已啟用執行緒數目的動態調整。 如果動態調整已停用，則要求的執行緒數目將會執行平列區域。 如果啟用動態調整，則要求的執行緒數目是可執行平列區域的執行緒數目上限。

如果在停用執行緒數目動態調整時遇到平列區域，而且針對平列區域所要求的執行緒數目大於執行時間系統可提供的數目，則程式的行為會是實作為定義。 例如，可能會中斷程式的執行，或是序列化平列區域。

連結 `omp_set_dynamic` 庫函式和 `OMP_DYNAMIC` 環境變數可用來啟用和停用動態調整執行緒數目。

在任何指定時間實際裝載執行緒的實體處理器數目是實作為定義。 一旦建立之後，小組中的執行緒數目會在該平列區域的持續時間內保持不變。 它可以由使用者明確變更，或由執行時間系統從一個平列區域自動變更為另一個區域。

平列區域動態範圍內所包含的語句會由每個執行緒執行，而且每個執行緒都可以執行與其他執行緒不同的語句路徑。 在平列區域的詞法範圍外發現的指示詞稱為孤立的指示詞。

在平列區域的結尾有隱含的關卡。 只有小組的主要執行緒會在平列區域結束時繼續執行。

如果執行平列區域之團隊中的執行緒遇到另一種平行結構，它會建立新的小組，而它會成為該新團隊的主伺服器。 預設會將嵌套的平列區域序列化。 因此，依預設，嵌套平列區域是由一個執行緒組成的小組執行。 您可以使用執行時間程式庫函數或環境變數來變更預設行為 `omp_set_nested` `OMP_NESTED` 。 不過，小組中執行嵌套平列區域的執行緒數目是實作為定義。

指示詞的限制如下 `parallel` ：

- 最多可以在指示詞 `if` 上出現一個子句。

- 不論 if 運算式或運算式內是否有任何副作用，都不 `num_threads` 會指定。

- 在 `throw` 平列區域內執行的必須讓執行在相同結構化區塊的動態範圍內繼續執行，而且必須由擲回例外狀況的相同執行緒捕捉。

- 只有單一 `num_threads` 子句可以出現在指示詞上。 `num_threads`運算式會在平列區域的內容之外進行評估，而且必須評估為正整數值。

- `if`未指定 and 子句的評估順序 `num_threads` 。

### <a name="cross-references"></a>交叉參考

- `private`、 `firstprivate` 、 `default` 、 `shared` 、 `copyin` 和 `reduction` 子句 ([區段 2.7.2](#272-data-sharing-attribute-clauses)) 
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) 環境變數
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) 程式庫函數
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) 環境變數
- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) 函式
- [OMP_NESTED](4-environment-variables.md#44-omp_nested) 環境變數
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function) 程式庫函數

## <a name="24-work-sharing-constructs"></a>2.4 工作共用結構

工作共用結構會將相關語句的執行分散到遇到它的團隊成員之間。 工作共用指示詞不會啟動新的執行緒，而且對工作共用結構的進入沒有隱含的屏障。

小組中每個執行緒所遇到的工作共用結構和指示詞順序都 `barrier` 必須相同。

OpenMP 定義下列工作共用結構，而這些結構將在下列各節中說明：

- [for](#241-for-construct) 指示詞
- [sections](#242-sections-construct) 指示詞
- [single](#243-single-construct) 指示詞

### <a name="241-for-construct"></a>用於結構的2.4。1

指示詞 `for` 會識別反復的工作共用結構，此結構會指定將平行執行相關聯之迴圈的反復專案。 `for`迴圈的反復專案會分散到已存在於小組中的執行緒，並執行其所系結的平行結構。 結構的語法如下所示 `for` ：

```cpp
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

子句是下列其中一項：

- `private(`*變數清單*`)`
- `firstprivate(`*變數清單*`)`
- `lastprivate(`*變數清單*`)`
- `reduction(`*運算子* `:`*變數清單*`)`
- `ordered`
- `schedule(`*種類*[ `,` *chunk_size*]`)`
- `nowait`

指示詞會對 `for` 對應迴圈的結構施加限制 `for` 。 具體來說，對應的 `for` 迴圈必須有標準圖形：

`for (`*init-expr* `;`*var 邏輯-op b* `;`*增量-expr*`)`

*init-expr*<br/>
下列其中之一：

- *var*  = *lb*
- *整數類型的 var*  = *lb*

*增量-expr*<br/>
下列其中之一：

- `++`*var*
- *var*`++`
- `--`*var*
- *var*`--`
- *var* `+=`*增量*
- *var* `-=`*增量*
- *var* `=`*var* `+`*增量*
- *var* `=`*增量* `+`*var*
- *var* `=`*var* `-`*增量*

*無 功*<br/>
帶正負號的整數變數。 如果這個變數是共用的，就會在期間隱含地成為私用 `for` 。 請勿在語句主體內修改此變數 `for` 。 除非已指定變數 `lastprivate` ，否則迴圈之後的值會不定。

*邏輯 op*<br/>
下列其中之一：

- `<`
- `<=`
- `>`
- `>=`

*lb*、 *b*和 *增量*<br>
迴圈不變的整數運算式。 評估這些運算式時，不會進行同步處理，因此任何評估的副作用都會產生不定的結果。

標準格式允許在進入迴圈時計算迴圈反覆運算次數。 這項計算是在整數升階之後，以 *var*型別中的值來進行。 尤其是，如果 *b* `-` *lb* `+` *增量* 的值無法以該類型表示，則結果為不定。 此外，如果 *邏輯 op* 是 `<` 或 `<=` ，則在迴圈的每個反復專案上， *增量-expr* 都必須讓 *var* 增加。   如果 *邏輯 op* 是 `>` 或 `>=` ，則在迴圈的每個反復專案上， *增量-expr* 都必須讓 *var* 變得較小。

`schedule`子句會指定如何在 `for` 小組的執行緒之間劃分迴圈的反覆運算。 程式的正確性不能相依于哪個執行緒執行特定的反復專案。 *Chunk_size*的值（如果指定的話）必須是具有正值的迴圈非變異整數運算式。 評估此運算式時，不會進行同步處理，因此任何評估的副作用都會產生不定的結果。 排程 *種類* 可以是下列其中一個值：

資料表2-1： `schedule` 子句 *種類* 值

|值|描述|
|-|-|
|static|當 `schedule(static,` 指定 *chunk_size*時 `)` ，會將反復專案分成 *chunk_size*所指定大小的區塊。 區塊會以迴圈配置資源的方式，以迴圈方式指派給小組中的執行緒，並以執行緒編號的順序來進行。 如果未指定 *chunk_size* ，則會將反復專案空間分割成大小大約相等的區塊，並將一個區塊指派給每個執行緒。|
|動態|當 `schedule(dynamic,` 指定 *chunk_size*時，會將反復專案 `)` 分成一連串的區塊，每個區塊都包含 *chunk_size* 反復專案。 每個區塊都會指派給等待指派的執行緒。 執行緒會執行反復專案的區塊，然後等候其下一個指派，直到沒有任何區塊被指派為止。 要指派的最後一個區塊可能會有較少的反覆運算次數。 當未指定 *chunk_size* 時，它會預設為1。|
|引導|當 `schedule(guided,` 指定 *chunk_size*時，會將反復專案 `)` 指派給區塊中大小減少的執行緒。 當執行緒完成其指派的反覆運算區塊時，會以動態方式指派另一個區塊，直到無剩下為止。 針對 *chunk_size* 1，每個區塊的大小大約是未指派的反復專案數目除以執行緒數目。 這些大小幾乎會以指數方式減少為1。 對於值為*k*大於1的*chunk_size* ，大小幾乎會以指數方式減少為*k*，差別在於最後一個區塊可能會有小於*k*的反覆運算。 當未指定 *chunk_size* 時，它會預設為1。|
|執行階段|當您 `schedule(runtime)` 指定時，有關排程的決策會延後到執行時間。 您可以藉由設定環境變數，在執行時間選擇區塊的排程 *種類* 和大小 `OMP_SCHEDULE` 。 如果未設定此環境變數，則產生的排程為實作為定義。 當  `schedule(runtime)` 指定時，不能指定 *chunk_size* 。|

如果沒有明確定義的 `schedule` 子句，預設值 `schedule` 就是實作為定義。

符合 OpenMP 規範的程式不應依賴特定排程來進行正確的執行。 程式不應依賴符合上述描述的排程 *種類* ，因為在不同編譯器之間可能會有不同的排程 *類型* 。 描述可以用來選取適用于特定情況的排程。

當指示詞系結 `ordered` 至結構時，子句必須存在 `ordered` `for` 。

`for`除非指定了子句，否則結構的結尾會有隱含的屏障 `nowait` 。

指示詞的限制如下 `for` ：

- `for`迴圈必須是結構化區塊，此外，它的執行不能由 **`break`** 語句終止。

- 與指示詞相關聯之迴圈的迴圈控制運算式值， `for` `for` 對於小組中的所有線程都必須相同。

- `for`迴圈反覆運算變數必須有帶正負號的整數類型。

- 指示詞 `schedule` 上只可以出現單一子句 `for` 。

- 指示詞 `ordered` 上只可以出現單一子句 `for` 。

- 指示詞 `nowait` 上只可以出現單一子句 `for` 。

- 如果發生 *chunk_size*、 *lb*、 *b*或 *增量* 運算式內的任何副作用，就不會指定它。

- 小組中所有線程的 *chunk_size* 運算式值都必須相同。

#### <a name="cross-references"></a>交叉參考

- `private`、 `firstprivate` 、 `lastprivate` 和 `reduction` 子句 ([區段 2.7.2](#272-data-sharing-attribute-clauses)) 
- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule) 環境變數
- 已[排序](#266-ordered-construct)的結構
- [schedule](d-using-the-schedule-clause.md) 子句

### <a name="242-sections-construct"></a>2.4.2 區段結構

指示詞 `sections` 會識別 noniterative 工作共用結構，以指定要在小組中的執行緒之間分割的一組結構。 每個區段都會由小組中的執行緒執行一次。 指示詞的語法如下所示 `sections` ：

```cpp
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

子句是下列其中一項：

- `private(`*變數清單*`)`
- `firstprivate(`*變數清單*`)`
- `lastprivate(`*變數清單*`)`
- `reduction(`*運算子* `:`*變數清單*  `)`
- `nowait`

每個區段前面都有一個指示詞 `section` ，雖然 `section` 第一個區段的指示詞是選擇性的。 指示詞必須出現在指示詞的 `section` 詞法範圍內 `sections` 。 `sections`除非已指定，否則在結構結尾會有隱含的屏障 `nowait` 。

指示詞的限制如下 `sections` ：

- 指示詞不能出現在指示詞的 `section` 詞法範圍之外 `sections` 。

- 指示詞 `nowait` 上只可以出現單一子句 `sections` 。

#### <a name="cross-references"></a>交叉參考

- `private`、 `firstprivate` 、 `lastprivate` 和 `reduction` 子句 ([區段 2.7.2](#272-data-sharing-attribute-clauses)) 

### <a name="243-single-construct"></a>2.4.3 單一結構

指示詞 `single` 會識別一種結構，以指定相關聯的結構化區塊只由小組中的一個執行緒執行， (不一定是主執行緒) 。 指示詞的語法如下所示 `single` ：

```cpp
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

子句是下列其中一項：

- `private(`*變數清單*`)`
- `firstprivate(`*變數清單*`)`
- `copyprivate(`*變數清單*`)`
- `nowait`

`single`除非已指定子句，否則結構後面會有隱含的屏障 `nowait` 。

指示詞的限制如下 `single` ：

- 指示詞 `nowait` 上只可以出現單一子句 `single` 。
- `copyprivate`子句不得搭配 `nowait` 子句使用。

#### <a name="cross-references"></a>交叉參考

- `private`、 `firstprivate` 和 `copyprivate` 子句 ([區段 2.7.2](#272-data-sharing-attribute-clauses)) 

## <a name="25-combined-parallel-work-sharing-constructs"></a>2.5 合併的平行工作共用結構

合併的平行工作共用結構是用來指定只有一個工作共用結構的平列區域的快捷方式。 這些指示詞的語法與明確指定指示詞， `parallel` 後面接著單一工作共用結構相同。

下列各節說明合併的平行工作共用結構：

- 指示詞[的 parallel](#251-parallel-for-construct)
- [parallel sections](#252-parallel-sections-construct) 指示詞

### <a name="251-parallel-for-construct"></a>2.5.1 平行處理結構

`parallel for`指示詞是 `parallel` 僅包含單一指示詞之區域的快捷方式 `for` 。 指示詞的語法如下所示 `parallel for` ：

```cpp
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

這個指示詞允許指示詞和指示詞的所有子句 `parallel` `for` （除了 `nowait` 子句以外）都具有相同的意義和限制。 此語義與明確指定指示詞後面緊接著指示詞的方式相同 `parallel` `for` 。

#### <a name="cross-references"></a>交叉參考

- [parallel](#23-parallel-construct) 指示詞
- [for](#241-for-construct) 指示詞
- [Data attribute 子句](#272-data-sharing-attribute-clauses)

### <a name="252-parallel-sections-construct"></a>2.5.2 平行區段結構

指示詞會 `parallel sections` 提供快捷方式形式來指定 `parallel` 只有單一指示詞的區域 `sections` 。 此語義與明確指定指示詞後面緊接著指示詞的方式相同 `parallel` `sections` 。 指示詞的語法如下所示 `parallel sections` ：

```cpp
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

*子句*可以是和指示詞所接受的其中一個 `parallel` 子句 `sections` ，但子句除外 `nowait` 。

#### <a name="cross-references"></a>交叉參考

- [parallel](#23-parallel-construct) 指示詞
- [sections](#242-sections-construct) 指示詞

## <a name="26-master-and-synchronization-directives"></a>2.6 主機和同步處理指示詞

下列各節將說明：

- [主要](#261-master-construct) 結構
- [重要](#262-critical-construct) 結構
- [屏障](#263-barrier-directive) 指示詞
- 不可部分完成[的結構](#264-atomic-construct)
- [flush](#265-flush-directive) 指示詞
- 已[排序](#266-ordered-construct)的結構

### <a name="261-master-construct"></a>2.6.1 主要結構

指示詞 `master` 會識別結構，此結構會指定由小組的主要執行緒所執行的結構化區塊。 指示詞的語法如下所示 `master` ：

```cpp
#pragma omp master new-linestructured-block
```

小組中的其他執行緒不會執行相關聯的結構化區塊。 在主要結構的進入或離開時，不會有隱含的關卡。

### <a name="262-critical-construct"></a>2.6.2 關鍵結構

`critical`指示詞會識別一次將關聯的結構化區塊執行限制為單一線程的結構。 指示詞的語法如下所示 `critical` ：

```cpp
#pragma omp critical [(name)]  new-linestructured-block
```

選擇性的 *名稱* 可用來識別重要區域。 用來識別重要區域的識別碼具有外部連結，而且位於與標籤、標記、成員和一般識別碼所使用的命名空間不同的命名空間中。

執行緒會在關鍵區域的開頭等候，直到沒有其他執行緒在程式) 中的任何位置執行重要區域 (任何相同的名稱。 所有未命名的指示詞都會 `critical` 對應到相同的未指定名稱。

### <a name="263-barrier-directive"></a>2.6.3 關卡指示詞

指示詞會 `barrier` 同步處理小組中的所有線程。 當遇到此狀況時，小組中的每個執行緒都會等候，直到所有其他執行緒都達到這個點為止。 指示詞的語法如下所示 `barrier` ：

```cpp
#pragma omp barrier new-line
```

當小組中的所有線程都遇到屏障之後，小組中的每個執行緒都會開始在關卡指示詞之後平行執行語句。 因為指示詞沒有 `barrier` C 語言語句作為語法的一部分，所以在程式內的放置有一些限制。 如需正式文法的詳細資訊，請參閱 [附錄 C](c-openmp-c-and-cpp-grammar.md)。下列範例說明這些限制。

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

`atomic`指示詞可確保特定記憶體位置會以不可部分完成的方式更新，而不會將其公開到多個同時寫入執行緒的可能性。 指示詞的語法如下所示 `atomic` ：

```cpp
#pragma omp atomic new-lineexpression-stmt
```

Expression 語句必須有下列其中一種形式：

- *x binop* `=`*expr*
- *x*`++`
- `++` *x*
- *x*`--`
- `--` *x*

在上述運算式中：

- *x* 是具有純量類型的左值運算式。

- *expr* 是具有純量類型的運算式，而且不會參考 *x*所指定的物件。

- *binop* 不是多載的運算子，而且是、、、、、、、 `+` `*` `-` `/` `&` `^` `|` `<<` 或 `>>` 。

雖然它是執行定義的，不論是否以具有相同唯一名稱的指示詞來取代所有指示詞，指示詞都 `atomic` `critical` 能提供*name* `atomic` 更佳的優化。 您通常可以使用硬體指示，以最少的額外負荷執行不可部分完成的更新。

只有 *x* 所指定之物件的載入和儲存是不可部分完成的; *運算式* 的評估不是不可部分完成的。 為了避免競爭情形，在平行位置的所有更新都應該使用指示詞來保護 `atomic` ，但已知不會有競爭情況的情況除外。

指示詞的限制如下 `atomic` ：

- 在整個程式中，所有對儲存位置 x 的不可部分完成參考都必須有相容的類型。

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

`flush`指示詞（不論是否為明確或隱含）都會指定需要執行的「跨執行緒」序列點，以確保小組中的所有線程都有一致的特定物件 (在記憶體中) 指定。 這表示，參考這些物件的運算式先前的評估已完成，而且後續的評估尚未開始。 例如，編譯器必須將物件的值從暫存器還原至記憶體，而硬體可能需要將寫入緩衝區排清至記憶體，並從記憶體重載物件的值。

指示詞的語法如下所示 `flush` ：

```cpp
#pragma omp flush [(variable-list)]  new-line
```

如果需要同步處理的物件都可以由變數指定，則可以在選擇性的 *變數清單*中指定這些變數。 如果指標出現在 *變數清單*中，指標本身就會排清，而非指標所參考的物件。

`flush`不含*變數清單*的指示詞會同步處理所有共用物件，但無法存取具有自動儲存期間的物件。  (這種情況可能會有比 `flush` 具有*變數清單*更多的額外負荷。 ) 不含變數清單的指示詞 `flush` 適用于下列*variable-list*指示詞：

- `barrier`
- 進入或離開 `critical`
- 進入或離開 `ordered`
- 進入或離開 `parallel`
- 離開時 `for`
- 離開時 `sections`
- 離開時 `single`
- 進入或離開 `parallel for`
- 進入或離開 `parallel sections`

如果有子句，則不隱含指示詞 `nowait` 。 請注意，指示詞 `flush` 不會針對下列任何一項隱含地隱含：

- 進入至 `for`
- 進入或離開 `master`
- 進入至 `sections`
- 進入至 `single`

存取具有 volatile 限定型別之物件值的參考，其行為就如同在 `flush` 先前的序列點指定該物件的指示詞。 修改具有 volatile 限定型別之物件值的參考，其行為就如同在 `flush` 後續序列點指定該物件的指示詞。

因為指示詞沒有 `flush` C 語言語句作為語法的一部分，所以在程式內的放置有一些限制。 如需正式文法的詳細資訊，請參閱 [附錄 C](c-openmp-c-and-cpp-grammar.md)。下列範例說明這些限制。

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

指示詞的限制如下 `flush` ：

- 指示詞中指定的變數 `flush` 不能有參考型別。

### <a name="266-ordered-construct"></a>2.6.6 排序的結構

指示詞後面的結構化區塊會依照在 `ordered` 連續迴圈中執行反覆運算的順序來執行。 指示詞的語法如下所示 `ordered` ：

```cpp
#pragma omp ordered new-linestructured-block
```

指示詞 `ordered` 必須在或結構的動態範圍內 `for` `parallel for` 。 結構所系結的或指示詞 `for` `parallel for` `ordered` 必須具有 `ordered` 指定的子句，如 [2.4.1 一節](#241-for-construct)中所述。 在 `for` 使用子句執行或結構時，會嚴格地以執行迴圈的循序執行的 `parallel for` 順序來 `ordered` `ordered` 執行結構。

指示詞的限制如下 `ordered` ：

- 具有結構的迴圈反復專案不能多次 `for` 執行相同的排序指示詞，也不能執行一個以上的指示詞 `ordered` 。

## <a name="27-data-environment"></a>2.7 資料環境

本節提供指示詞和數個子句，用於在平列區域執行期間控制資料環境，如下所示：

- 您可以使用 [threadprivate](#271-threadprivate-directive) 指示詞，將檔案範圍、命名空間範圍或靜態區塊範圍變數，提供給執行緒的本機。

- 您可以在指示詞上指定的子句，以控制平行或工作共用結構持續時間內變數的共用屬性，如 [2.7.2 一節](#272-data-sharing-attribute-clauses)中所述。

### <a name="271-threadprivate-directive"></a>2.7.1 threadprivate 指示詞

指示詞 `threadprivate` 會將命名空間、命名空間範圍或靜態區塊範圍變數指定于執行緒的私用 *變數清單* 中。 *變數清單* 是以逗號分隔的變數清單，這些變數沒有不完整的類型。 指示詞的語法如下所示 `threadprivate` ：

```cpp
#pragma omp threadprivate(variable-list) new-line
```

每一份 `threadprivate` 變數都會初始化一次，在程式中第一次參考該複本之前，在程式中未指定的位置，以一般方式 (也就是，因為主要複本將會在程式的序列執行中初始化) 。 請注意，如果在變數的明確初始化運算式中參考物件 `threadprivate` ，並且在第一次參考變數之前修改物件的值，則不會指定行為。

如同任何私用變數，執行緒不能參考另一個執行緒的 `threadprivate` 物件複本。 在序欄區域和程式的主要區域中，參考將會指向主要執行緒的物件複本。

第一個平列區域執行之後， `threadprivate` 只有當動態執行緒機制已停用，而且所有平列區域的執行緒數目保持不變時，才會保證物件中的資料保持不變。

指示詞的限制如下 `threadprivate` ：

- 檔案 `threadprivate` 範圍或命名空間範圍變數的指示詞必須出現在任何定義或宣告之外，而且必須在其清單中任何變數的所有參考之前。

- 在檔案或命名空間範圍之指示詞的 *變數清單* 中，每個變數都 `threadprivate` 必須參考在述詞前面的檔案或命名空間範圍中的變數宣告。

- `threadprivate`靜態區塊範圍變數的指示詞必須出現在變數的範圍內，而不是在嵌套的範圍中。 指示詞必須在其清單中所有變數的所有參考之前。

- 在區塊範圍中，指示詞的 *變數清單* 中的每個變數，都 `threadprivate` 必須參考到述詞前面的相同範圍中的變數宣告。 變數宣告必須使用靜態儲存類別規範。

- 如果在某個轉譯單位的指示詞中指定了變數 `threadprivate` ，它必須在其宣告所在的 `threadprivate` 每個轉譯單位中，于指示詞中指定。

- `threadprivate`變數不能出現在 `copyin` 、、 `copyprivate` `schedule` 、 `num_threads` 或 `if` 子句以外的任何子句中。

- `threadprivate`變數位址不是位址常數。

- `threadprivate`變數不能有不完整的類型或參考型別。

- `threadprivate`具有非 POD 類別類型的變數必須具有可存取且明確的複製函式（如果使用明確的初始化運算式來宣告）。

下列範例說明如何修改初始化運算式中出現的變數可能會導致未指定的行為，以及如何使用輔助物件和複製函式來避免這個問題。

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

#### <a name="cross-references"></a>交叉參考

- [動態執行緒](3-run-time-library-functions.md#317-omp_set_dynamic-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) 環境變數

### <a name="272-data-sharing-attribute-clauses"></a>2.7.2 資料共用屬性子句

數個指示詞接受子句，可讓使用者在區域期間控制變數的共用屬性。 共用屬性子句只適用于出現子句之指示詞的詞法範圍中的變數。 並非所有的指令程式都允許使用下列所有子句。 在特定指示詞上有效的子句清單會與指示詞一起描述。

如果遇到平行或工作共用結構時，變數是可見的，且在共用屬性子句或指示詞中未指定變數 `threadprivate` ，則變數是共用的。 共用平列區域動態範圍內所宣告的靜態變數。 堆積配置的記憶體 (例如， `malloc()` 在 c 或 c + + 中使用，或在 **`new`** c + +) 中使用運算子是共用的。 不過 (此記憶體的指標可以是私用或共用的。在平列區域動態範圍內宣告的自動儲存持續時間 ) 變數是私用的。

大部分的子句都會接受 *變數清單* 引數，這是可見的變數清單（以逗號分隔）。 如果資料共用屬性子句中參考的變數具有衍生自範本的型別，而且程式中沒有該變數的其他參考，則行為是未定義的。

指示詞子句內出現的所有變數都必須是可見的。 子句可依需要重複執行，但在多個子句中不能指定任何變數，但變數可以同時在 `firstprivate` 和子句中指定 `lastprivate` 。

下列各節說明資料共用屬性子句：

- [私人](#2721-private)
- [firstprivate](#2722-firstprivate)
- [lastprivate](#2723-lastprivate)
- [共用](#2724-shared)
- [預設值](#2725-default)
- [減少](#2726-reduction)
- [copyin](#2727-copyin)
- [copyprivate](#2728-copyprivate)

#### <a name="2721-private"></a>2.7.2.1 private

`private`子句會將變數清單中的變數宣告為私用至小組中的每個執行緒。 子句的語法如下所示 `private` ：

```cpp
private(variable-list)
```

在子句中指定之變數的行為如下所示 `private` 。 具有自動儲存期的新物件會配置給此結構。 新物件的大小和對齊方式取決於變數的類型。 此配置會針對小組中的每個執行緒執行一次，並視需要針對類別物件叫用預設的函式;否則初始值為不定值。  變數所參考的原始物件在進入結構時有不定的值，不能在結構的動態範圍內修改，而且在從結構結束時有不定值。

在指示詞結構的詞法範圍中，變數會輔助線程所配置的新私用物件。

子句的限制如下 `private` ：

- 在子句中指定類別類型的變數 `private` 必須具有可存取且明確的預設的函式。

- `private` **`const`** 除非子句具有具有成員的類別類型，否則在子句中指定的變數不能有限定型別 `mutable` 。

- 在子句中指定的變數 `private` 不能有不完整的類型或參考型別。

- 在指示詞的子句中出現的變數， `reduction` `parallel` 不能指定于系結 `private` 至平行結構之工作共用指示詞的子句中。

#### <a name="2722-firstprivate"></a>2.7.2.2 firstprivate

`firstprivate`子句提供子句所提供之功能的超集合 `private` 。 子句的語法如下所示 `firstprivate` ：

```cpp
firstprivate(variable-list)
```

*變數清單*中指定的變數具有 `private` 子句語義，如[2.7.2.1 一節](#2721-private)中所述。 初始化或結構會像是線上程執行結構之前，在每個執行緒執行一次一樣。 若是 `firstprivate` 平行結構上的子句，新私用物件的初始值就是原始物件的值，該物件會在遇到它的執行緒的平行結構之前立即存在。 針對 `firstprivate` 工作共用結構上的子句，執行工作共用結構之每個執行緒的新私用物件初始值，就是在相同執行緒遇到工作共用結構的時間點之前存在的原始物件的值。 此外，針對 c + + 物件，每個執行緒的新私用物件都會從原始物件進行複製。

子句的限制如下 `firstprivate` ：

- 在子句中指定的變數 `firstprivate` 不能有不完整的類型或參考型別。

- 具有指定為之類別型別的變數 `firstprivate` ，必須具有可存取且明確的複製函式。

- 在平列區域內或出現在指示詞子句中的變數， `reduction` `parallel` 不能指定于系結 `firstprivate` 至平行結構之工作共用指示詞的子句中。

#### <a name="2723-lastprivate"></a>2.7.2.3 lastprivate

`lastprivate`子句提供子句所提供之功能的超集合 `private` 。 子句的語法如下所示 `lastprivate` ：

```cpp
lastprivate(variable-list)
```

*變數清單*中指定的變數具有 `private` 子句語義。 當 `lastprivate` 子句出現在識別工作共用結構的指示詞上時，會將每個變數的值 `lastprivate` ，從關聯迴圈的最後一個反復專案，或從詞法上的最後一個區段指示詞，指派給變數的原始物件。 未在或的最後一個反復專案中指派值的 `for` 變數 `parallel for` ，或由或指示詞的詞法上最後一個區段在 `sections` `parallel sections` 結構之後具有不定值。 未指派的子陣列在結構之後也有不定的值。

子句的限制如下 `lastprivate` ：

- 適用的所有限制 `private` 。

- 具有指定為之類別型別的變數 `lastprivate` ，必須具有可存取且明確的複製指派運算子。

- 在平列區域內或出現在指示詞子句中的變數， `reduction` `parallel` 不能指定于系結 `lastprivate` 至平行結構之工作共用指示詞的子句中。

#### <a name="2724-shared"></a>2.7.2.4 shared

這個子句會在小組中的所有線程之間共用出現在 *變數清單* 中的變數。 小組內的所有線程都會存取相同的變數儲存區域 `shared` 。

子句的語法如下所示 `shared` ：

```cpp
shared(variable-list)
```

#### <a name="2725-default"></a>2.7.2.5 default

`default`子句可讓使用者影響變數的資料共用屬性。 子句的語法如下所示 `default` ：

```cpp
default(shared | none)
```

指定相當 `default(shared)` 于明確列出子句中每個目前可見的變數 `shared` ，除非它是 `threadprivate` 或 **`const`** 限定的。 如果沒有明確的 `default` 子句，預設行為會與指定的相同 `default(shared)` 。

指定 `default(none)` 時，對於平行結構的詞彙範圍中的每個變數參考，至少必須符合下列其中一項條件：

- 變數會明確列在包含參考之結構的資料共用屬性子句中。

- 變數是在平行結構內宣告的。

- 變數為 `threadprivate` 。

- 變數具有 **`const`** -限定型別。

- 變數是迴圈的迴圈控制變數，此變數會 `for` 緊接在或指示詞的後面 `for` `parallel for` ，而且變數參考會出現在迴圈內。

在包含的指示詞的 `firstprivate` 、或子句上指定變數，會在封 `lastprivate` `reduction` 入內容中造成變數的隱含參考。 這類隱含參考也會受限於上述的需求。

只有一個 `default` 子句可以在指示詞上指定 `parallel` 。

您可以使用、、、和子句來覆寫變數的預設資料共用屬性 `private` `firstprivate` `lastprivate` `reduction` `shared` ，如下列範例所示：

```cpp
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```

#### <a name="2726-reduction"></a>2.7.2.6 reduction

這個子句會使用運算子*op*來減少出現在*變數清單*中的純量變數。 子句的語法如下所示 `reduction` ：

`reduction(`*op* `:`*變數清單*`)`

通常會針對具有下列其中一種形式的語句來指定縮減：

- *x* `=` *x* *op* *運算式*
- *x* *binop* `=` *運算式*
- *x* `=` *運算式* *op* *x*  (但減法) 除外
- *x*`++`
- `++` *x*
- *x*`--`
- `--` *x*

其中：

*x*<br/>
清單中指定的其中一個縮減變數。

*變數清單*<br/>
純量縮減變數的逗號分隔清單。

*expr*<br/>
沒有參考 *x*之純量類型的運算式。

*主管*<br/>
不是多載的運算子，而是、、、、、、或中的一個 `+` `*` `-` `&` `^` `|` `&&` `||` 。

*binop*<br/>
不是多載的運算子，而是、、、、或其中之一 `+` `*` `-` `&` `^` `|` 。

以下是子句的範例 `reduction` ：

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

如範例所示，運算子可能會隱藏在函式呼叫內。 使用者應該小心，在子句中指定的運算子 `reduction` 符合縮減作業。

雖然運算子的右運算元 `||` 在此範例中沒有任何副作用，但它們是允許的，但應該謹慎使用。 在這種情況下，在執行迴圈時保證不會發生的副作用可能會在平行執行期間發生。 發生這種差異的原因可能是反覆運算的執行順序不確定。

運算子用來判斷編譯器為了減少而使用之任何私用變數的初始值，以及判斷最終運算子。 指定運算子會明確允許縮減語句在結構的詞法範圍之外。 您 `reduction` 可以在指示詞上指定任何數目的子句，但變數最多可能會出現在 `reduction` 該指示詞的一個子句中。

會為每個執行緒建立一個變數 *清單* 中每個變數的私用複本，就如同 `private` 已使用子句一樣。 私用複本會根據運算子進行初始化 (請參閱下表) 。

在指定子句的區域結尾 `reduction` ，原始物件會更新，以反映其原始值與每個私用複本的最終值（使用指定的運算子）的結果。 除了減法) 之外，減少運算子全都 (關聯，而編譯器可以自由地重新關聯最終值的計算。  (會新增減法縮減的部分結果，以形成最終值。 ) 

當第一個執行緒到達包含子句時，原始物件的值會變成不定，而在縮減計算完成之前保持不變。  一般情況下，計算會在結構結束時完成;但是，如果在 `reduction` 也套用的結構上使用子句，則在 `nowait` 執行關卡同步處理以確保所有線程都已完成子句之前，原始物件的值會保持不定 `reduction` 。

下表列出有效的運算子及其標準初始化值。 實際的初始化值將會與縮減變數的資料類型一致。

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

子句的限制如下 `reduction` ：

- 子句中的變數類型 `reduction` 必須適用于縮減運算子，但不允許指標類型和參考型別。

- 在子句中指定的變數 `reduction` 不得為 **`const`** 限定的。

- 在平列區域內或出現在指示詞子句中的變數， `reduction` `parallel` 不能指定于系結 `reduction` 至平行結構之工作共用指示詞的子句中。

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

`copyin`子句會提供一種機制，為 `threadprivate` 執行平列區域之小組中的每個執行緒，指派相同的值給變數。 針對子句中所指定的每個變數 `copyin` ，會將小組主要執行緒中的變數值複製到平列區域開頭的執行緒私用複本（如同指派）。 子句的語法如下所示 `copyin` ：

```cpp

copyin(
variable-list
)
```

子句的限制如下 `copyin` ：

- 在子句中指定的變數 `copyin` 必須具有可存取、明確的複製指派運算子。

- 在子句中指定的變數 `copyin` 必須是 `threadprivate` 變數。

#### <a name="2728-copyprivate"></a>2.7.2.8 copyprivate

`copyprivate`子句會提供一種機制，讓您使用私用變數，將某個小組成員的值廣播到另一個成員。 在提供這類共用變數時，這是使用共用變數作為值的替代方法 (例如，在每個層級上需要不同變數的遞迴中) 。 `copyprivate`子句只可出現在指示詞上 `single` 。

子句的語法如下所示 `copyprivate` ：

```cpp

copyprivate(
variable-list
)
```

`copyprivate`子句在其變數清單中之變數的影響會在執行與結構相關聯的結構化區塊之後 `single` ，以及小組中的任何執行緒在結構結束時離開關卡。 然後，在小組中的所有其他執行緒中，針對 *變數清單*中的每個變數，該變數就會變成定義 (如同藉由指派) ，以及執行結構結構化區塊之執行緒中對應變數的值。

子句的限制如下 `copyprivate` ：

- 在子句中指定的變數 `copyprivate` 不能出現在同一個指示詞的 `private` 或子句中 `firstprivate` `single` 。

- 如果 `single` `copyprivate` 在平列區域的動態範圍中遇到具有子句的指示詞，則子句中指定的所有變數在封入內容中都 `copyprivate` 必須是私用的。

- 在子句中指定的變數 `copyprivate` 必須有可存取的明確複製指派運算子。

## <a name="28-directive-binding"></a>2.8 指示詞系結

指示詞的動態繫結必須遵守下列規則：

- 、、、和指示詞會系結 `for` 至動態封入 `sections` （如果有的話 `single` `master` `barrier` `parallel` ），而不論 `if` 該指示詞上可能存在的任何子句值為何。 如果目前未執行任何平列區域，則指示詞由只由主執行緒組成的小組執行。

- 指示詞會系結 `ordered` 至動態封閉 `for` 。

- 指示詞 `atomic` 會針對所有線程中的指示詞強制執行獨佔存取 `atomic` ，而不只是目前的小組。

- 指示詞 `critical` 會針對所有線程中的指示詞強制執行獨佔存取 `critical` ，而不只是目前的小組。

- 指示詞永遠不能系結至最接近動態封入範圍之外的任何指示詞 `parallel` 。

## <a name="29-directive-nesting"></a>2.9 指示詞的嵌套

指示詞的動態嵌套必須遵守下列規則：

- 在 `parallel` 另一個邏輯內部動態 `parallel` 建立的指示詞會建立新的小組，而這只是由目前的執行緒所組成，除非已啟用嵌套平行處理原則。

- `for`系結 `sections` `single` 至相同的、和指示詞 `parallel` 不允許嵌套在彼此內部。

- `critical` 具有相同名稱的指示詞不能嵌套在彼此內部。 請注意，此限制不足以防止鎖死。

- `for`如果指示詞系結 `sections` 至相同的區域，則 `single` 不允許在、和區域的動態範圍中使用、和指示詞 `critical` `ordered` `master` `parallel` 。

- `barrier` 如果指示詞系結至相同的區域，則不允許在 `for` 、、 `ordered` `sections` 、 `single` 、 `master` 和 `critical` 區域 `parallel` 的動態範圍中使用指示詞。

- `master` 如果指示詞系結 `for` 至與工作共用指示詞 `sections` `single` `master` 相同的，則不允許在、和指示詞的動態範圍中使用指示詞 `parallel` 。

- `ordered` 如果指示詞系結至與區域相同的區域，則不允許在區域的動態範圍中使用指示詞 `critical` `parallel` 。

- 當在平列區域外部執行時，也允許在平列區域內以動態方式執行時，所允許的任何指示詞。 以動態方式在使用者指定的平列區域外部執行時，指示詞是由只有主要執行緒的小組執行。
