---
title: C. OpenMP C 和C++文法
ms.date: 01/16/2019
ms.assetid: 97a878ce-1533-47f7-a134-66fcbff48524
ms.openlocfilehash: 85e18161079b49e83cc9fedb3184ee220c889e75
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362942"
---
# <a name="c-openmp-c-and-c-grammar"></a>C. OpenMP C 和C++文法

[C.1 標記法](#c1-notation)<br/>
[C.2 規則](#c2-rules)

## <a name="c1-notation"></a>C.1 標記法

文法規則包含非-終端機中，名稱後面接著冒號，後面接著取代替代項目不同行上。

語法的運算式詞彙<sub>opt</sub>指出一詞是選擇性內取代。

語法的運算式*詞彙*<sub>optseq</sub>相當於*詞彙 seq*<sub>選擇</sub>與下列其他規則：

*term-seq*:  
&nbsp;&nbsp;&nbsp;&nbsp;*term*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*term-seq* *term*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*term-seq*   `,` *term*

## <a name="c2-rules"></a>C.2 規則

標記法是由 C 標準的 6.1 一節所述。 此文法附錄顯示基底語言文法擴充 OpenMP c 和C++指示詞。

**/\* 在C++(ISO/IEC 14882:1998) \*/**

*statement-seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*陳述式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp-directive*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement-seq statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement-seq openmp-directive*

**/\* 在 C90 (ISO/IEC 9899:1990) \*/**

*statement-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*陳述式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp-directive*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement-list 陳述式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*陳述式清單 openmp 指示詞*

**/\* 在 C99 (ISO/IEC 9899:1999) \*/**

*區塊項目*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*宣告*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*陳述式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp-directive*

**/\* 標準的陳述式 \*/**

*statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp-construct*

*openmp 建構*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parallel-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*for-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sections-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*single-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parallel-for-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parallel-sections-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*master-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*critical-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*atomic-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ordered-construct*

*openmp 指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*barrier-directive*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*flush-directive*

*結構化區塊*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*陳述式*

*parallel-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*平行指示詞結構化區塊*

*平行指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel` *parallel-clause*<sub>optseq</sub> *new-line*

*平行子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-parallel-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*

*唯一平行子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `if (` *expression*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `num_threads (` *expression*   `)`

*用於建構*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*指示詞的反覆項目陳述式*

*指示詞的*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp for` *for-clause*<sub>optseq</sub> *new-line*

*for 子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-for-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*唯一 for 子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `ordered`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `schedule (` *schedule-kind*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `schedule (` *schedule-kind*   `,` *expression*   `)`

*排程類型*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `static`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `dynamic`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `guided`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `runtime`

*區段建構*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*區段指示詞區段範圍*

*區段指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp sections` *sections-clause*<sub>optseq</sub> *new-line*

*區段子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*區段範圍*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*{ section-sequence }*

*區段順序*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*section-directive*<sub>opt</sub> *structured-block*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*section-sequence section-directive structured-block*

*區段指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp section` *new-line*

*單一建構*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*單一指示詞結構化區塊*

*單一指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp single` *single-clause*<sub>optseq</sub> *new-line*

*單一子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*parallel-for-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*平行指示詞的反覆項目陳述式*

*平行的指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel for` *parallel-for-clause*<sub>optseq</sub> *new-line*

*平行 for 子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-parallel-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-for-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*

*parallel-sections-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*平行 sections 指示詞區段範圍*

*parallel-sections-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel sections` *parallel-sections-clause*<sub>optseq</sub> *new-line*

*parallel-sections-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-parallel-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*

*主要建構*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*master 指示詞結構化區塊*

*master 指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp master` *new-line*

*critical 建構*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*critical 指示詞結構化區塊*

*critical 指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp critical` *region-phrase*<sub>opt</sub> *new-line*

*區域片語*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*（識別碼）*

*barrier 指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp barrier` *new-line*

*atomic 建構*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*atomic 指示詞的運算式陳述式*

*atomic 指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp atomic` *new-line*

*flush 指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp flush` *flush-vars*<sub>opt</sub> *new-line*

*排清變數*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(variable-list)*

*排序建構*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*排序指示詞結構化區塊*

*排序指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp ordered` *new-line*

**/\* 標準的宣告 \*/**

*宣告*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*threadprivate-directive*

*threadprivate 指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp threadprivate (` *variable-list*    `)` *new-line*

*data 子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `private (` *variable-list*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `copyprivate (`  *variable-list*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `firstprivate (`  *variable-list*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `lastprivate (` *variable-list*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `shared (` *variable-list*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `default ( shared )`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `default ( none )`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `reduction (`  *reduction-operator*    `:`  *variable-list*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `copyin (`  *variable-list*    `)`

*削減運算子*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;其中一種：   `+ \* - & ^ | && ||`

**/\* 在 C 中 \*/**

*變數清單*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*variable-list*   `,` *identifier*

**/\* 在C++ \*/**

*變數清單*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*id-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*variable-list*   `,` *id-expression*
