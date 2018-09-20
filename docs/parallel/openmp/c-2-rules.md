---
title: C.2 規則 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4d52fef7-3eb7-4480-a335-8ed48681092b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c5845a9125bb32254fc0c03b03e9b6076a086d1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404770"
---
# <a name="c2-rules"></a>C.2 規則

標記法是由 C 標準的 6.1 一節所述。 此文法附錄說明 OpenMP C 和 c + + 的指示詞的基底語言文法的延伸模組。

**/\* 在 c + + (ISO/IEC 14882:1998) \*/**

*陳述式 seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*陳述式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp 指示詞*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*陳述式 seq 陳述式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*陳述式 seq openmp 指示詞*

**/\* 在 C90 (ISO/IEC 9899:1990) \*/**

*statement-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*陳述式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp 指示詞*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement-list 陳述式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*陳述式清單 openmp 指示詞*

**/\* 在 C99 (ISO/IEC 9899:1999) \*/**

*區塊項目*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*宣告*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*陳述式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp 指示詞*

**/\* 標準的陳述式 \*/**

*statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp 建構*

*openmp 建構*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*平行建構*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*建構*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*區段建構*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*單一建構*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*平行 for 建構*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*平行區段建構*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*master 建構*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*critical 建構*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*atomic 建構*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*排序建構*

*openmp 指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*barrier 指示詞*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*flush 指示詞*

*結構化區塊*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*陳述式*

*平行建構*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*平行指示詞結構化區塊*

*平行指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp parallel** *平行子句*<sub>optseq</sub> *新行*

*平行子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*唯一平行子句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data 子句*

*唯一平行子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**如果 (** *運算式* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**num_threads (** *運算式* **)**

*用於建構*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*指示詞的反覆項目陳述式*

*指示詞的*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**針對 # pragma omp** *for 子句*<sub>optseq</sub> *新行*

*for 子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*唯一 for 子句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data 子句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nowait**

*唯一 for 子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**排序**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**排程 (** *排程種類* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**排程 (** *排程種類* **，** *運算式* **)**

*排程類型*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**靜態**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**動態**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**引導式**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**執行階段**

*區段建構*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*區段指示詞區段範圍*

*區段指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp 章節***各節子句*<sub>optseq</sub> *新行*

*區段子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data 子句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nowait**

*區段範圍*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*{區段順序}*

*區段順序*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*區段指示詞*<sub>opt</sub> *結構化區塊*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*區段順序區段指示詞結構化區塊*

*區段指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp 區段***新行*

*單一建構*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*單一指示詞結構化區塊*

*單一指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**單一的 # pragma omp** *單一子句*<sub>optseq</sub> *新行*

*單一子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data 子句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nowait**

*平行的建構*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*平行指示詞的反覆項目陳述式*

*平行的指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**針對平行的 # pragma omp** *平行 for 子句*<sub>optseq</sub> *新行*

*平行 for 子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*唯一平行子句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*唯一 for 子句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data 子句*

*平行區段建構*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*平行 sections 指示詞區段範圍*

*平行 sections 指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp 平行處理區段***平行區段子句*<sub>optseq</sub> *新行*

*平行區段子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*唯一平行子句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data 子句*

*主要建構*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*master 指示詞結構化區塊*

*master 指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp 母片***新行*

*critical 建構*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*critical 指示詞結構化區塊*

*critical 指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**重要的 # pragma omp** *區域片語*<sub>opt</sub> *新行*

*區域片語*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*（識別碼）*

*barrier 指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp 屏障***新行*

*atomic 建構*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*atomic 指示詞的運算式陳述式*

*atomic 指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**不可部分完成的 # pragma omp** *新行*

*flush 指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**排清的 # pragma omp** *排清變數*<sub>opt</sub> *新行*

*排清變數*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*（變數清單）*

*排序建構*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*排序指示詞結構化區塊*

*排序指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp 的訂購***新行*

**/\* 標準的宣告 \*/**

*宣告*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*threadprivate 指示詞*

*threadprivate 指示詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp threadprivate (** *變數清單***)** *新行* 

*data 子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**私用 (** *變數清單* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**copyprivate (***變數清單***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**firstprivate (***變數清單***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**lastprivate (** *變數清單***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**共用 (** *變數清單* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**預設 （共用）**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**預設 （無）**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**減少 (***削減運算子***:***變數清單***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**copyin (***變數清單***)** 

*削減運算子*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;其中一個：  **+  \* -& ^ &#124; （& s) （& s)&#124;&#124;**

**/\* 在 C 中 \*/**

*變數清單*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*變數清單* **，** *識別碼*

**/\* 在 c + + \*/**

*變數清單*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*變數清單* **，** *識別碼運算式*