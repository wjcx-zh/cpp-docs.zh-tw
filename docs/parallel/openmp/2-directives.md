---
title: 2. 指示詞
ms.date: 01/18/2019
ms.assetid: d1a69374-6c03-45fb-8c86-e91cea8adae8
ms.openlocfilehash: 125d2d83b277e62d007e3a208e426ea717d52790
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087336"
---
# <a name="2-directives"></a>2.指示詞

指示詞根據`#pragma`C 和 c + + 標準中所定義的指示詞。  支援 OpenMP C 和 c + + API 的編譯器會包含命令列選項，就會啟動，並允許所有 OpenMP 編譯器指示詞的解譯。

## <a name="21-directive-format"></a>2.1 指示詞格式

OpenMP 指示詞的語法正式指定文法[附錄 C](c-openmp-c-and-cpp-grammar.md)，和非正式地，如下所示：

```cpp
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

每個指示詞開頭`#pragma omp`，以降低與具有相同名稱的其他 （非 OpenMP 或廠商延伸模組與 OpenMP） pragma 指示詞衝突的可能性。 指示詞的其餘部分都遵循編譯器指示詞的 C 和 c + + 標準的慣例。 特別是，使用空白字元之前和之後`#`，和有時也泛空白字元必須用來分隔指示詞中的文字。 前置處理語彙基元`#pragma omp`限於巨集取代。

指示詞會區分大小寫。 指示詞中子句出現的順序並不大。 如有需要受限於每個子句描述中所列的限制，可能會重複上指示詞子句。 如果*變數清單*會出現在子句中，它必須指定只有變數。 只有一個*指示詞名稱*可以指定每個指示詞。  比方說，不允許下列指示詞：

```cpp
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

OpenMP 指示詞套用至最多一個後續陳述式，它必須是結構化的區塊。

## <a name="22-conditional-compilation"></a>2.2 條件式編譯

`_OPENMP`巨集名稱指 OpenMP 相容實作十進位常數*yyyymm*，它會是年份和月份的已核准的規格。 這個巨集不能主旨`#define`或`#undef`前置處理器指示詞。

```cpp
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

如果廠商定義與 OpenMP 的擴充功能，它們就可以指定其他預先定義的巨集。

## <a name="23-parallel-construct"></a>2.3 parallel 建構

下列指示詞定義在平行區域，是由多個執行緒以平行方式執行的程式的區域。 這個指示詞是開始平行執行的基本建構。

```cpp
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block
```

*子句*是下列其中之一：

- `if(` *scalar-expression* `)`
- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `default(shared | none)`
- `shared(` *variable-list* `)`
- `copyin(` *variable-list* `)`
- `reduction(` *operator* `:`  *variable-list* `)`
- `num_threads(` *integer-expression* `)`

執行緒取得平行建構，如果其中一個下列的情況下，則為 true 時會建立的執行緒小組：

- 否`if`出現子句時。
- `if`運算式會評估為非零值。

此執行緒會成為小組成員，0，執行緒數目的主要執行緒和小組成員，包括主要執行緒中中的所有執行緒以平行方式都執行的區域。 如果值`if`運算式為零，序列化的區域。

若要判斷要求的執行緒數目，下列規則會被視為順序。 第一個符合其條件的規則將會套用：

1. 如果`num_threads`子句已存在，則整數運算式的值是所要求的執行緒數目。

1. 如果`omp_set_num_threads`已呼叫程式庫函式，則是最近執行的呼叫中引數的值是所要求的執行緒數目。

1. 如果環境變數`OMP_NUM_THREADS`定義，則此環境變數的值是所要求的執行緒數目。

1. 如果使用任何上述方法，然後要求的執行緒數目是由實作定義。

如果`num_threads`出現子句時，則它會取代所要求的執行緒數目`omp_set_num_threads`程式庫函式或`OMP_NUM_THREADS`環境變數只會針對它套用到平行區域。 稍後平行區域不會受到它。

執行平行區域的執行緒數目也取決於是否已啟用動態調整執行緒數目。 如果已停用動態調整，要求的執行緒數目會執行平行的區域。 如果動態調整已啟用要求的執行緒數目是可能執行平行區域的執行緒數目上限。

如果在平行區域為止已停用動態調整執行緒數目，而要求的平行區域的執行緒數目大於可以提供執行階段系統的數字，該程式的行為是實作定義。 實作可能，比方說，中斷執行程式，或它可以將平行區域進行序列化。

`omp_set_dynamic`程式庫函式和`OMP_DYNAMIC`環境變數可用來啟用和停用動態調整執行緒數目。

實體處理器實際上裝載在任何指定時間的執行緒數目是由實作定義。 建立之後，在小組中的執行緒數目維持不變，平行區域的持續期間。 明確的使用者或自動執行階段系統從一個平行區域到另一個，就可以進行變更。

每個執行緒中，執行包含在平行區域的動態範圍內的陳述式，並每個執行緒可以執行的陳述式的路徑不同於其他執行緒。 發生在平行區域的語彙範圍外的指示詞被指被遺棄的指示詞。

沒有隱含的障礙，在平行區域的結尾。 只有小組的主要執行緒會繼續執行在平行區域的結尾。

如果小組執行平行的區域中的執行緒發生另一個平行建構，它會建立新的小組，它會變成該新的小組的主要。 根據預設，會序列化巢狀平行區域。 如此一來，根據預設，巢狀平行區域是由一個執行緒所組成的小組執行。 可能會使用執行階段程式庫函式來變更預設行為`omp_set_nested`環境變數或`OMP_NESTED`。 不過，在小組執行巢狀平行區域的執行緒數目是由實作定義。

若要限制`parallel`指示詞如下所示：

- 最多一個`if`子句可以出現在指示詞。

- 它具有未指定任何是否端效果置於 if 運算式或`num_threads`運算式就會發生。

- A`throw`執行在平行區域必須造成才能繼續在相同的結構化區塊，動態範圍內執行，且必須由相同的執行緒擲回例外狀況攔截到。

- 只有一個`num_threads`子句可以出現在指示詞。 `num_threads`運算式會評估平行區域中，內容之外，並且必須評估為正整數值。

- 評估順序`if`和`num_threads`子句並未指定。

### <a name="cross-references"></a>交互參照

- `private``firstprivate`， `default`， `shared`， `copyin`，並`reduction`子句 ([區段 2.7.2](#272-data-sharing-attribute-clauses))
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)環境變數
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)程式庫函式
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)環境變數
- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) function
- [OMP_NESTED](4-environment-variables.md#44-omp_nested)環境變數
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function)程式庫函式

## <a name="24-work-sharing-constructs"></a>2.4 工作共用建構

工作共用建構會將執行相關聯的陳述式，會遇到相同的小組成員之間。 工作共用指示詞不會啟動新的執行緒，並在工作共用建構的項目上沒有任何隱含的障礙。

將一連串工作共用建構和`barrier`遇到的指示詞必須是相同的小組中的每個執行緒。

OpenMP 定義下列的工作共用建構，並請依照下列各節會說明這些建構：

- [針對](#241-for-construct)指示詞
- [區段](#242-sections-construct)指示詞
- [單一](#243-single-construct)指示詞

### <a name="241-for-construct"></a>2.4.1 for 建構

`for`指示詞會識別反覆工作共用建構，指定相關聯的迴圈的反覆項目，則會以平行方式執行。 反覆項目`for`迴圈會分散到存在於小組執行平行建構，它會繫結的執行緒。 語法`for`建構如下所示：

```cpp
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

子句可以是下列其中一項：

- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `lastprivate(` *variable-list* `)`
- `reduction(` *operator* `:` *variable-list* `)`
- `ordered`
- `schedule(` *kind* [`,` *chunk_size*] `)`
- `nowait`

`for`指示詞會置於對應的結構中的限制`for`迴圈。 具體來說，對應`for`迴圈必須有標準的圖形：

`for (` *init-expr* `;` *var  logical-op  b* `;` *incr-expr* `)`

*init-expr*<br/>
下列其中一項：

- *var* = *lb*
- *integer-type var* = *lb*

*incr-expr*<br/>
下列其中一項：

- `++` *var*
- *var* `++`
- `--` *var*
- *var* `--`
- *var* `+=` *incr*
- *var* `-=` *incr*
- *var* `=` *var* `+` *incr*
- *var* `=` *incr* `+` *var*
- *var* `=` *var* `-` *incr*

*var*<br/>
帶正負號的整數變數。 如果此變數會否則共用，它會隱含地變成私用的持續期間`for`。 請勿修改此變數的主體內`for`陳述式。 除非指定變數`lastprivate`，不定迴圈之後其值。

*logical-op*<br/>
下列其中一項：

- `<`
- `<=`
- `>`
- `>=`

*lb*， *b*，和*incr*<br>
迴圈不變的整數運算式。 沒有任何同步處理期間評估這些運算式中，因此任何已評估的副作用產生未定的結果。

標準格式可讓要計算項目，以迴圈的迴圈反覆項目數目。 型別中的值進行這項計算*var*之後整數提升。 特別是當值*b* `-` *lb* `+` *incr* ，型別，結果是無法確定無法表示。 此外，如果*邏輯 op*是`<`或`<=`，然後*incr expr*必須造成*var*增加在迴圈的每個反覆項目。   如果*邏輯 op*是`>`或是`>=`，然後*incr expr*必須造成*var*迴圈的每個反覆運算上取得較小。

`schedule`子句會指定如何的反覆項目`for`迴圈會分配給小組的執行緒。 程式的正確性不得相依於哪一個執行緒執行的特定反覆項目。 值*chunk_size*，如果指定，必須是正數值為迴圈而異的整數運算式。 沒有任何同步處理期間評估此運算式中，因此任何已評估的副作用產生未定的結果。 排程*種類*可以是下列值之一：

表 2-1:`schedule`子句*種類*值

|||
|-|-|
|靜態|當`schedule(static,` *chunk_size* `)`指定，反覆項目分成區塊的指定大小*chunk_size*。 區塊會以靜態方式指派順序執行緒編號以循環配置資源方式小組中的執行緒。 若未*chunk_size*指定時，反覆運算空間會分割成區塊 （chunk） 的其中一個指派給每個執行緒的區塊大小，大約等於。|
|動態|當`schedule(dynamic,` *chunk_size* `)`指定反覆項目可分為區塊，每個都包含一連串*chunk_size*反覆項目。 每個區塊會指派給正在等候指派的執行緒。 執行緒執行的反覆項目區塊，然後等到其下一步 的指派，任何區塊會保持指派。 要指派的最後一個區塊可能會有較少的反覆項目。 若未*chunk_size*指定，則會預設為 1。|
|引導式|當`schedule(guided,` *chunk_size* `)`指定，以減少大小的區塊中的執行緒指派反覆項目。 當執行緒完成其指派的區塊的反覆項目時，它有動態指派另一個區塊，直到沒有任何保留。 針對*chunk_size*為 1，每個區塊的大小是大約未指派除以的執行緒數目的反覆項目數目。 這些大小幾乎以指數方式減少為 1。 針對*chunk_size*具有值*k*大於 1，大小為幾乎以指數方式減少*k*，差異在於最後一個區塊可能會有少於*k*反覆項目。 若未*chunk_size*指定，則會預設為 1。|
|runtime|當`schedule(runtime)`指定時，相關的排程會延後執行階段決定。 排程*種類*可以在執行階段選擇的區塊的大小，藉由設定環境變數和`OMP_SCHEDULE`。 如果未設定這個環境變數，產生的排程是由實作定義。 當`schedule(runtime)`指定，則*chunk_size*不得指定。|

沒有明確定義`schedule`子句，則預設`schedule`是由實作定義。

OpenMP 相容的程式不應該依賴正確執行的特定排程。 程式不應該依賴排程*種類*符合精確地提供上述的描述，因為它是可以在相同的排程的實作有變化*種類*跨不同的編譯器。 描述可用來選取的排程，適用於特定的情況。

`ordered`子句必須要有的時機`ordered`指示詞將繫結至`for`建構。

結尾沒有隱含的障礙`for`建構，除非`nowait`指定子句。

若要限制`for`指示詞如下所示：

- `for`迴圈必須是結構化的區塊中，且，此外，其執行必須不結束`break`陳述式。

- 值，迴圈的控制運算式`for`相關聯的迴圈`for`指示詞必須是相同的小組中的所有執行緒。

- `for`迴圈反覆項目變數必須具有帶正負號的整數類型。

- 只有一個`schedule`子句可能會出現在`for`指示詞。

- 只有一個`ordered`子句可能會出現在`for`指示詞。

- 只有一個`nowait`子句可能會出現在`for`指示詞。

- 如果未指定，或任何側邊效果內的頻率*chunk_size*， *lb*， *b*，或*incr*運算式就會發生。

- 值*chunk_size*運算式必須是相同的小組中的所有執行緒。

#### <a name="cross-references"></a>交互參照

- `private``firstprivate`， `lastprivate`，並`reduction`子句 ([區段 2.7.2](#272-data-sharing-attribute-clauses))
- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule)環境變數
- [排序](#266-ordered-construct)建構
- [排程](d-using-the-schedule-clause.md)子句

### <a name="242-sections-construct"></a>2.4.2 區段建構

`sections`指示詞會識別 noniterative 的工作共用建構，指定一組要在小組中的執行緒之間分割的建構。 由小組中的執行緒中，每個區段會執行一次。 語法`sections`指示詞時，如下所示：

```cpp
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

子句可以是下列其中一項：

- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `lastprivate(` *variable-list* `)`
- `reduction(` *operator* `:`  *variable-list* `)`
- `nowait`

每個區段前面加上`section`指示詞，雖然`section`指示詞是選擇性的第一個區段。 `section`指示詞必須出現的語彙範圍內`sections`指示詞。 結尾沒有隱含的障礙`sections`建構，除非`nowait`指定。

若要限制`sections`指示詞如下所示：

- A`section`指示詞不得出現的語彙範圍外`sections`指示詞。

- 只有一個`nowait`子句可能會出現在`sections`指示詞。

#### <a name="cross-references"></a>交互參照

- `private``firstprivate`， `lastprivate`，並`reduction`子句 ([區段 2.7.2](#272-data-sharing-attribute-clauses))

### <a name="243-single-construct"></a>2.4.3 single 建構

`single`指示詞會識別指定小組 （不一定是主要執行緒） 中只有一個執行緒執行相關聯的結構化的區塊的建構。 語法`single`指示詞時，如下所示：

```cpp
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

子句可以是下列其中一項：

- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `copyprivate(` *variable-list* `)`
- `nowait`

沒有隱含的障礙之後,`single`建構，除非`nowait`指定子句。

若要限制`single`指示詞如下所示：

- 只有一個`nowait`子句可能會出現在`single`指示詞。
- `copyprivate`子句不能搭配`nowait`子句。

#### <a name="cross-references"></a>交互參照

- `private``firstprivate`，並`copyprivate`子句 ([一節 2.7.2](#272-data-sharing-attribute-clauses))

## <a name="25-combined-parallel-work-sharing-constructs"></a>2.5 合併的平行工作共用建構

結合的平行工作共用建構是用於指定有只有一個工作共用建構在平行區域的捷徑。 這些指示詞的語意為明確指定相同`parallel`指示詞後面接著單一的工作共用建構。

下列各節說明的結合的平行工作共用建構：

- [針對平行](#251-parallel-for-construct)指示詞
- [平行處理區段](#252-parallel-sections-construct)指示詞

### <a name="251-parallel-for-construct"></a>2.5.1 parallel for 建構

`parallel for`指示詞是捷徑`parallel`只包含一個單一的區域`for`指示詞。 語法`parallel for`指示詞時，如下所示：

```cpp
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

這個指示詞允許的所有子句`parallel`指示詞和`for`指示詞，除了`nowait`子句中，使用相同的意義和限制。 都與明確指定相同的語意`parallel`指示詞後面緊跟著`for`指示詞。

#### <a name="cross-references"></a>交互參照

- [平行](#23-parallel-construct)指示詞
- [針對](#241-for-construct)指示詞
- [資料屬性子句](#272-data-sharing-attribute-clauses)

### <a name="252-parallel-sections-construct"></a>2.5.2 平行處理區段建構

`parallel sections`指示詞來指定提供快顯表單`parallel`都只能有單一的區域`sections`指示詞。 都與明確指定相同的語意`parallel`指示詞後面緊跟著`sections`指示詞。 語法`parallel sections`指示詞時，如下所示：

```cpp
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

*子句*可以是其中一個接受子句`parallel`並`sections`指示詞，除了`nowait`子句。

#### <a name="cross-references"></a>交互參照

- [平行](#23-parallel-construct)指示詞
- [區段](#242-sections-construct)指示詞

## <a name="26-master-and-synchronization-directives"></a>2.6 主版和同步處理的指示詞

下列各節說明：

- [主要](#261-master-construct)建構
- [重要](#262-critical-construct)建構
- [屏障](#263-barrier-directive)指示詞
- [不可部分完成](#264-atomic-construct)建構
- [排清](#265-flush-directive)指示詞
- [排序](#266-ordered-construct)建構

### <a name="261-master-construct"></a>2.6.1 master 建構

`master`指示詞會識別指定小組的主要執行緒所執行的結構化的區塊的建構。 語法`master`指示詞時，如下所示：

```cpp
#pragma omp master new-linestructured-block
```

在小組中的其他執行緒不會執行相關聯的結構化的區塊。 沒有任何隱含的障礙，項目，或從 master 建構結束。

### <a name="262-critical-construct"></a>2.6.2 critical 建構

`critical`指示詞會識別相關聯的結構化區塊執行的限制為單一執行緒，一次的建構。 語法`critical`指示詞時，如下所示：

```cpp
#pragma omp critical [(name)]  new-linestructured-block
```

選擇性*名稱*可能用來識別重要區域。 用來識別重要區域的識別項具有外部連結，並會在不同的標籤、 標記、 成員和一般識別項使用的命名空間的命名空間。

在關鍵區域的開頭的執行緒等候，直到沒有其他執行緒正在執行 （在程式中） 具有相同名稱的關鍵區域。 所有未命名`critical`指示詞對應至相同的未指定名稱。

### <a name="263-barrier-directive"></a>2.6.3 barrier 指示詞

`barrier`指示詞會在一個小組中的所有執行緒同步都處理。 遇到時，在小組中的每個執行緒會等候直到所有的其他人已經達到這個點為止。 語法`barrier`指示詞時，如下所示：

```cpp
#pragma omp barrier new-line
```

在小組中的所有執行緒都遇到屏障之後，在小組中的每個執行緒就會開始之後 barrier 指示詞，以平行方式執行的陳述式。 因為`barrier`指示詞沒有 C 語言陳述式，其語法的一部分，有一些限制，它在程式內的位置上。 如需正式文法的詳細資訊，請參閱[附錄 C](c-openmp-c-and-cpp-grammar.md)。下列範例會說明這些限制。

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

### <a name="264-atomic-construct"></a>2.6.4 atomic 建構

`atomic`指示詞可讓您確保特定記憶體位置會以不可分割的方式，更新，而不是將其公開到可能的多個同時撰寫執行緒。 語法`atomic`指示詞時，如下所示：

```cpp
#pragma omp atomic new-lineexpression-stmt
```

運算陳述式必須具有下列格式之一：

- *x binop* `=` *expr*
- *x* `++`
- `++` *x*
- *x* `--`
- `--` *x*

在上述的運算式：

- *x*是純量類型的左值運算式。

- *expr*是純量類型，使用運算式，其並未參考所指定的物件*x*。

- *binop*無法多載的運算子，而且是其中一個`+`， `*`， `-`， `/`， `&`， `^`， `|`， `<<`，或`>>`。

雖然它是由實作定義是否實作會取代所有`atomic`使用指示詞`critical`指示詞具有相同的唯一*名稱*，則`atomic`指示詞允許更好的最佳化. 通常是硬體指示可執行不可部分完成的更新具有最少額外負荷。

只有負載和所指定的物件存放區*x*是不可部分完成; 評估*expr*並非不可部分完成。 若要避免競爭情形，所有更新的位置，以平行方式應該都受到`atomic`指示詞，除了已知為免費的競爭情形。

若要限制`atomic`指示詞如下所示：

- 在整個程式的儲存體位置 x 不可部分完成的所有參考，都才能有相容的類型。

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

`flush`指示詞，是否明確或隱含的請指定"跨執行緒 「 序列點的實作，才能確保小組中的所有執行緒都有某些指定的物件 （如下） 在記憶體中的一致檢視。 這表示先前評估的運算式參考那些物件都已完成，而且還沒開始後續評估。 比方說，編譯器必須從暫存器物件的值還原記憶體中，並且硬體可能需要排清寫入緩衝區記憶體並重新載入記憶體中物件的值。

語法`flush`指示詞時，如下所示：

```cpp
#pragma omp flush [(variable-list)]  new-line
```

如果需要同步處理的物件可以所有指定的變數，則這些變數可以指定選擇性*變數清單*。 指標是否存在於*變數清單*，指標本身會排清，不是物件指標參考。

A`flush`指示詞，而不需要*變數清單*同步所有共用的物件，但無法存取的物件不具有自動儲存期。 (這是可能會有更多的額外負荷比`flush`具有*變數清單*。)A`flush`指示詞，而不需要*變數清單*隱含的下列指示詞：

- `barrier`
- 在進入和結束 `critical`
- 在進入和結束 `ordered`
- 在進入和結束 `parallel`
- 在結束時，從 `for`
- 在結束時，從 `sections`
- 在結束時，從 `single`
- 在進入和結束 `parallel for`
- 在進入和結束 `parallel sections`

如果不隱含的指示詞`nowait`出現子句時。 請注意，`flush`指示詞不隱含的下列任一項：

- 在項目 `for`
- 在進入或結束 `master`
- 在項目 `sections`
- 在項目 `single`

存取具有 volatile 限定類型之物件的值參考行為好像`flush`指示詞指定該物件在前一個序列點。 修改 volatile 限定類型之物件的值參考行為好像`flush`指示詞指定該物件在後續的序列點。

因為`flush`指示詞沒有 C 語言陳述式，其語法的一部分，有一些限制，它在程式內的位置上。 如需正式文法的詳細資訊，請參閱[附錄 C](c-openmp-c-and-cpp-grammar.md)。下列範例會說明這些限制。

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

若要限制`flush`指示詞如下所示：

- 中指定的變數`flush`指示詞不能是參考型別。

### <a name="266-ordered-construct"></a>2.6.6 ordered 建構

結構化的區塊下列`ordered`指示詞會循序迴圈執行反覆項目中的順序執行。 語法`ordered`指示詞時，如下所示：

```cpp
#pragma omp ordered new-linestructured-block
```

`ordered`指示詞必須是動態的範圍內`for`或`parallel for`建構。 `for`或`parallel for`的指示詞`ordered`建構繫結必須`ordered`中所述指定子句[區段 2.4.1](#241-for-construct)。 在執行`for`或`parallel for`建構包含`ordered`子句，`ordered`建構會嚴格執行中執行，所以在循序執行迴圈的順序。

若要限制`ordered`指示詞如下所示：

- 迴圈的反覆項目`for`建構必須不會一次以上相同的 ordered 指示詞執行，而且只能執行一個以上的`ordered`指示詞。

## <a name="27-data-environment"></a>2.7 資料環境

此章節提供的指示詞和數個子句，如下所示的平行區域，在執行期間控制資料環境：

- A [threadprivate](#271-threadprivate-directive)指示詞可讓執行緒本機檔案範圍、 命名空間範圍或靜態的區塊範圍變數。

- 您可以在要平行或工作共用建構期間控制變數的共用屬性的指示詞指定的子句中所述[一節 2.7.2](#272-data-sharing-attribute-clauses)。

### <a name="271-threadprivate-directive"></a>2.7.1 threadprivate 指示詞

`threadprivate`指示詞讓具名的檔案範圍、 命名空間範圍或靜態的區塊範圍變數中指定*變數清單*執行緒私用。 *變數清單*是沒有不完整類型的變數的逗號分隔清單。 語法`threadprivate`指示詞時，如下所示：

```cpp
#pragma omp threadprivate(variable-list) new-line
```

每一份`threadprivate`變數會初始化一次，在未指定的時間點之前的第一個參考到該複本，計畫和一般方式 （亦即，當主要複本會初始化序列執行的程式中）。 請注意，如果在明確的初始設定式中參考物件的`threadprivate`變數和物件的值一份變數的第一個參考之前遭到修改，則行為是未指定。

如有任何私用變數，執行緒絕不能參考另一個執行緒的副本`threadprivate`物件。 在序列地區和程式的主要區域中，參考是物件的主要執行緒的複本。

執行第一個平行區域中的資料之後`threadprivate`物件一定會保存只当動態執行緒機制已停用，而如果執行緒數目維持不變，所有的平行區域。

若要限制`threadprivate`指示詞如下所示：

- A`threadprivate`檔案範圍或命名空間範圍變數的指示詞必須出現任何定義或宣告中，外部，而且必須語彙前面清單中的任何變數的所有參考。

- 在每個變數*變數清單*的`threadprivate`在語彙上位於指示詞的檔案或命名空間範圍的變數宣告必須參考指示詞檔案或命名空間的範圍。

- A`threadprivate`靜態的區塊範圍變數的指示詞必須出現在變數的範圍內，而不是在巢狀範圍。 指示詞語彙必須在所有參考任何變數都之前在其清單中。

- 在每個變數*變數清單*的`threadprivate`區塊範圍中的指示詞必須參考相同語彙前面的指示詞的範圍中的變數宣告。 變數宣告都必須使用靜態儲存類別規範。

- 如果變數中指定`threadprivate`指示詞在一個轉譯單位中，您必須指定在`threadprivate`宣告它的每一個轉譯單位的指示詞。

- A`threadprivate`變數不得出現在以外的任何子句`copyin`， `copyprivate`， `schedule`， `num_threads`，或`if`子句。

- 位址`threadprivate`變數不是位址是否固定。

- A`threadprivate`變數不能是不完整的類型或參考型別。

- A`threadprivate`非 POD 類別類型的變數必須可存取且明確的複製建構函式，如果它使用明確的初始設定式宣告。

下列範例說明如何修改初始設定式中出現的變數可能會導致未指定的行為，以及如何使用輔助物件和複製建構函式，以避免這個問題。

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

#### <a name="cross-references"></a>交互參照

- [動態的執行緒](3-run-time-library-functions.md#317-omp_set_dynamic-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)環境變數

### <a name="272-data-sharing-attribute-clauses"></a>2.7.2 資料共用屬性子句

幾個指示詞會接受可讓使用者控制變數的共用屬性區域的持續時間的子句。 共用屬性子句僅適用於中子句出現的指示詞的語彙範圍的變數。 並非所有的下列子句允許所有指示詞。 適用於特定的指示詞的子句的清單將描述使用指示詞。

如果是變數，才會顯示平行或遇到工作共用建構，以及變數未共用屬性子句中指定或`threadprivate`指示詞，然後將變數共用。 在平行區域的動態範圍內宣告的靜態變數會在共用中。 堆積配置的記憶體 (例如，使用`malloc()`C 或 c + + 或`new`中 c + + 運算子) 會共用。 （指標給這個記憶體，不過，可以是私人或共用）。在平行區域的動態範圍內宣告的自動儲存期的變數都是私用。

大部分的子句接受*變數清單*引數是以逗號分隔的清單會顯示的變數。 如果變數參考的資料共用屬性子句具有型別衍生自範本，而且不有任何其他程式中的該變數的參考，行為是未定義。

出現在指示詞子句後面的所有變數都必須都是可見的。 子句可能會重複，如有需要但可能在多個子句中，指定任何變數，不同之處在於變數可以指定在這兩`firstprivate`和`lastprivate`子句。

下列各節描述的資料共用屬性子句：

- [private](#2721-private)
- [firstprivate](#2722-firstprivate)
- [lastprivate](#2723-lastprivate)
- [shared](#2724-shared)
- [default](#2725-default)
- [reduction](#2726-reduction)
- [copyin](#2727-copyin)
- [copyprivate](#2728-copyprivate)

#### <a name="2721-private"></a>2.7.2.1 private

`private`子句宣告為私用小組的每個執行緒的變數清單中的變數。 語法`private`子句如下所示：

```cpp
private(variable-list)
```

中指定的變數的行為`private`子句如下所示。 具有自動儲存期的新物件配置的建構。 大小和新物件的對齊會取決於變數的類型。 此配置發生一次在小組中，每個執行緒和預設建構函式會叫用類別物件，如有必要，否則的初始值為未定。  原始變數所參考的物件具有不定值的建構的項目、 動態建構的範圍內，不得修改和不定值從建構在結束時。

中的指示詞的建構之語彙範圍內，變數會參考新的私用物件配置的執行緒。

若要限制`private`子句如下所示：

- 中指定的類別類型的變數`private`子句必須具有可存取且明確的預設建構函式。

- 中指定的變數`private`子句不能有`const`-限定型別，除非它具有類型的類別`mutable`成員。

- 中指定的變數`private`子句不能是不完整的類型或參考型別。

- 在出現的變數`reduction`子句`parallel`指示詞中不能指定`private`繫結至平行建構之工作共用指示詞子句。

#### <a name="2722-firstprivate"></a>2.7.2.2 firstprivate

`firstprivate`子句提供的所提供的功能超集`private`子句。 語法`firstprivate`子句如下所示：

```cpp
firstprivate(variable-list)
```

中指定的變數*變數清單*有`private`子句的語意，如中所述[區段 2.7.2.1](#2721-private)。 如同它已執行過一次每個執行緒，則建構的執行緒執行前，可發生初始化或建構。 針對`firstprivate`平行建構子句，新的私用物件的初始值是之前遇到執行緒的平行建構存在的原始物件的值。 針對`firstprivate`工作共用建構上的子句，每個執行緒執行的工作共用建構新的私用物件的初始值是存在的同一個執行緒發生的時間點之前的原始物件的值工作共用建構。 此外，對於 c + + 物件，每個執行緒的新私用物件是複製建構自原始物件。

若要限制`firstprivate`子句如下所示：

- 中指定的變數`firstprivate`子句不能是不完整的類型或參考型別。

- 指定為類別類型的變數`firstprivate`必須可存取且明確的複製建構函式。

- 在平行區域內的私用，或出現在中的變數`reduction`子句`parallel`指示詞中不能指定`firstprivate`繫結至平行建構之工作共用指示詞子句。

#### <a name="2723-lastprivate"></a>2.7.2.3 lastprivate

`lastprivate`子句提供的所提供的功能超集`private`子句。 語法`lastprivate`子句如下所示：

```cpp
lastprivate(variable-list)
```

中指定的變數*變數清單*有`private`子句的語意。 當`lastprivate`識別的工作共用的建構，而每個值在指示詞上出現子句`lastprivate`循序最後一個反覆項目相關聯的迴圈中，或最後一個語彙區段指示詞中，從變數指派給變數的原始物件。 未指派的最後一個反覆項目值的變數`for`或`parallel for`，或由語彙最後一節`sections`或`parallel sections`指示詞後建構, 具有下列不定值。 未指派的子物件也會建構後有不定值。

若要限制`lastprivate`子句如下所示：

- 所有的限制，如`private`套用。

- 指定為類別類型的變數`lastprivate`必須可存取且明確的複製指派運算子。

- 在平行區域內的私用，或出現在中的變數`reduction`子句`parallel`指示詞中不能指定`lastprivate`繫結至平行建構之工作共用指示詞子句。

#### <a name="2724-shared"></a>2.7.2.4 shared

這個子句共用中出現的變數*變數清單*小組中的所有執行緒之間。 在小組的所有執行緒都存取的相同儲存體區域`shared`變數。

語法`shared`子句如下所示：

```cpp
shared(variable-list)
```

#### <a name="2725-default"></a>2.7.2.5 default

`default`子句可讓使用者會影響變數的資料共用屬性。 語法`default`子句如下所示：

```cpp
default(shared | none)
```

指定`default(shared)`相當於明確列出每個中的目前可見變數`shared`子句，除非它是`threadprivate`或`const`-限定。 沒有明確`default`子句，預設行為是相同如果`default(shared)`所指定。

指定`default(none)`至少下列其中之一必須是針對至平行建構的語彙範圍中變數的每個參考，則為 true:

- 變數會明確地列出建構包含參考的資料共用屬性子句中。

- 在平行建構中宣告的變數。

- 變數是`threadprivate`。

- 變數具有`const`-限定型別。

- 變數是 for 迴圈控制變數`for`迴圈緊接`for`或`parallel for`指示詞，且變數參考會出現在迴圈內。

在指定的變數`firstprivate`， `lastprivate`，或`reduction`括住的指示詞子句會造成封入內容中的變數的隱含參考。 這類隱含的參考也限於上面所列的需求。

只有一個`default`您可以在指定子句`parallel`指示詞。

變數的預設資料共用屬性，可以使用覆寫`private`， `firstprivate`， `lastprivate`， `reduction`，和`shared`子句，如下列範例所示：

```cpp
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```

#### <a name="2726-reduction"></a>2.7.2.6 reduction

這個子句會減少執行上會出現在純量變數*變數清單*，與運算子*op*。 語法`reduction`子句如下所示：

`reduction(` *op* `:` *variable-list* `)`

減少通常被指定的陳述式，使用下列格式之一：

- *x* `=` *x* *op* *expr*
- *x* *binop* `=` *expr*
- *x* `=` *expr* *op* *x* （除了減法）
- *x* `++`
- `++` *x*
- *x* `--`
- `--` *x*

其中：

*x*<br/>
其中一個清單中指定削減變數。

*variable-list*<br/>
純量削減變數的逗號分隔清單。

*expr*<br/>
未參考的純量類型的運算式*x*。

*op*<br/>
無法多載的運算子，但其中一個`+`， `*`， `-`， `&`， `^`， `|`， `&&`，或`||`。

*binop*<br/>
無法多載的運算子，但其中一個`+`， `*`， `-`， `&`， `^`，或`|`。

以下是範例`reduction`子句：

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

此範例所示，操作員可能會隱藏函式呼叫。 使用者應該要小心中指定的運算子`reduction`子句與相符的削減作業。

雖然的右運算元`||`運算子在此範例中沒有任何副作用，它們允許的但應該小心使用。 在此情況下，平行執行期間可能發生有保證不會循序執行迴圈期間發生的副作用。 這項差異可能是因為反覆執行的順序為不定。

運算子用來判斷編譯器所使用，以減少任何私用變數的初始值，以及決定最終處理運算子。 明確指定運算子，可讓要建構的語彙範圍外的縮減陳述式。 任意數目的`reduction`子句可指定指示詞，但變數可能會出現在最多一個`reduction`該指示詞子句。

每個變數中的私用複本*變數清單*建立時，一個用於每個執行緒，如同`private`子句已使用。 根據運算子初始化私用複本 （請參閱下表）。

為其區域結尾`reduction`指定子句，原始的物件會更新以反映合併其原始的值，與每個使用指定的運算子的私用複本的最終值的結果。 減少運算子 （除了減）、 所有關聯，而且編譯器可以自由重新關聯，以計算最終的值。 （以形成最後的值會加入減法減少部分結果）。

當第一個執行緒到達包含子句，並保持不變，減少計算完成之前，原始物件的值會變成不定。  一般來說，計算會完整建構; 結尾不過，如果`reduction`子句可在其中建構`nowait`是另外套用原始物件的值直到不定已執行的屏障同步處理，以確保所有執行緒都已都完成`reduction`子句。

下表列出有效的運算子和其標準的初始化值。 實際的初始化值會與削減變數的資料類型一致。

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

若要限制`reduction`子句如下所示：

- 中的變數類型`reduction`子句必須適用於削減運算子，不同之處在於永遠不會允許指標型別和參考型別。

- 中指定的變數`reduction`子句不能`const`-限定。

- 在平行區域內的私用，或出現在中的變數`reduction`子句`parallel`指示詞中不能指定`reduction`繫結至平行建構之工作共用指示詞子句。

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

`copyin`子句提供一個機制來指派相同的值，以`threadprivate`小組執行平行的區域中的每個執行緒的變數。 指定在每個變數`copyin`複製子句，在小組的主要執行緒中變數的值，如同是由指派執行緒私用複本，在平行區域的開頭。 語法`copyin`子句如下所示：

```cpp

copyin(
variable-list
)
```

若要限制`copyin`子句如下所示：

- 中指定的變數`copyin`子句必須具有可存取且明確的複製指派運算子。

- 中指定的變數`copyin`子句必須`threadprivate`變數。

#### <a name="2728-copyprivate"></a>2.7.2.8 copyprivate

`copyprivate`子句提供一個機制來使用私用變數從一小組的成員的值廣播到其他成員。 它是使用共用的變數值時提供這類共用的變數會很困難 （例如，在需要不同的變數，每個層級的遞迴函式） 的替代方案。 `copyprivate`子句只能出現在`single`指示詞。

語法`copyprivate`子句如下所示：

```cpp

copyprivate(
variable-list
)
```

效果`copyprivate`其變數清單中的變數上的子句執行相關聯的結構化區塊之後，就會發生`single`建構，以及之前的任何執行緒在小組中剩下屏障建構結尾。 然後，在小組中每個變數中的所有其他執行緒*變數清單*，該變數會變成 （如同依指派） 已定義的對應值的結構化執行建構的執行緒中的變數區塊。

若要限制`copyprivate`子句如下所示：

- 中指定的變數`copyprivate`子句不得出現在`private`或是`firstprivate`而言，同一個子句`single`指示詞。

- 如果`single`指示詞搭配`copyprivate`子句發生在平行區域的動態範圍中，所有的變數指定在`copyprivate`子句必須是私用的封入內容中。

- 中指定的變數`copyprivate`子句必須具有可存取模稜兩可的複製指派運算子。

## <a name="28-directive-binding"></a>2.8 指示詞的繫結

動態繫結的指示詞必須遵守下列規則：

- `for`， `sections`， `single`， `master`，並`barrier`指示詞將繫結至動態封閉`parallel`時，如果有的話，無論任何的值`if`子句可能會存在於該指示詞。 如果沒有平行區域目前正在執行中，只有主要執行緒所組成的小組所執行指示詞。

- `ordered`指示詞將繫結至動態封閉`for`。

- `atomic`指示詞會強制執行獨佔存取權，相對於`atomic`所有執行緒，而不只是目前的小組中的指示詞。

- `critical`指示詞會強制執行獨佔存取權，相對於`critical`所有執行緒，而不只是目前的小組中的指示詞。

- 指示詞可以永遠不會繫結至最接近以外的任何指示詞動態封入`parallel`。

## <a name="29-directive-nesting"></a>2.9 指示詞的巢狀結構

動態巢狀指示詞必須遵守下列規則：

- A`parallel`指示詞，以動態方式放到另一個`parallel`邏輯上會建立新的小組，目前的執行緒所組成，除非巢狀平行處理原則已啟用。

- `for``sections`，並`single`繫結至相同的指示詞`parallel`nelze vnořit do 彼此並不允許。

- `critical` nelze vnořit do 彼此不允許具有相同名稱的指示詞。 請注意，這項限制不足夠以避免產生死結。

- `for``sections`，並`single`指示詞不允許的動態範圍中`critical`， `ordered`，並`master`如果指示詞繫結至相同的區域`parallel`為區域。

- `barrier` 動態的範圍中不允許使用指示詞`for`， `ordered`， `sections`， `single`， `master`，和`critical`如果指示詞繫結至相同的區域`parallel`為區域。

- `master` 動態的範圍中不允許使用指示詞`for`， `sections`，並`single`指示詞如果`master`指示詞將繫結至相同`parallel`為工作共用指示詞。

- `ordered` 指示詞中的動態範圍，不允許`critical`如果指示詞繫結至相同的區域`parallel`為區域。

- 區域外部的平行執行時，也允許在平行區域內以動態方式執行時所允許的任何指示詞。 動態執行使用者指定的平行區域之外，會執行指示詞，只有主要執行緒所組成的小組。
