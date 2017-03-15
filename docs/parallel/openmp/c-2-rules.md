---
title: "C.2 規則 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 4d52fef7-3eb7-4480-a335-8ed48681092b
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C.2 規則
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

標記法節將說明 6.1 C 標準。 此文法附錄說明 OpenMP C 和 c + + 的指示詞的基本語言文法的延伸模組。  
  
 **/\* 在 c + + (ISO/IEC 14882:1998) \*/**  
  
 *陳述式 seq*:  
  
 *陳述式*  
  
 *openmp 指示詞*  
  
 *陳述式 seq 陳述式*  
  
 *陳述式 seq openmp 指示詞*  
  
 **/\* 在 C90 (ISO/IEC 9899:1990) \*/**  
  
 *陳述式清單*:  
  
 *陳述式*  
  
 *openmp 指示詞*  
  
 *statement-list 陳述式*  
  
 *陳述式清單 openmp 指示詞*  
  
 **/\* 在 C99 (ISO/IEC 9899:1999) \*/**  
  
 *區塊項目*:  
  
 *宣告*  
  
 *陳述式*  
  
 *openmp 指示詞*  
  
 *陳述式*:  
  
 **/\* 標準的陳述式 \*/**  
  
 *openmp 建構*  
  
 *openmp 建構*:  
  
 *平行建構*  
  
 *建構*  
  
 *區段建構*  
  
 *單一建構*  
  
 *平行 for 建構*  
  
 *平行區段建構*  
  
 *主要 construc*  
  
 *critical 建構*  
  
 *atomic 建構*  
  
 *排序建構*  
  
 *openmp 指示詞*:  
  
 *barrier 指示詞*  
  
 *flush 指示詞*  
  
 *結構化區塊*:  
  
 *陳述式*  
  
 *平行建構*:  
  
 *指示詞的平行化區塊*  
  
 *平行指示詞*:  
  
 **# pragma omp 平行**  *平行子句*optseq *新行*  
  
 *平行子句*:  
  
 *唯一平行子句*  
  
 *資料子句*  
  
 *唯一平行子句*:  
  
 **如果 (** *運算式* **)**  
  
 **num_threads (** *運算式* **)**  
  
 *用於建構*:  
  
 *指示詞的反覆運算陳述式*  
  
 *指示詞的*:  
  
 **# pragma omp 的** *for 子句*optseq *新行*  
  
 *for 子句*:  
  
 *唯一的子句*  
  
 *資料子句*  
  
 **nowait**  
  
 *唯一的子句*:  
  
 **排序**  
  
 **排程 (** *排程種類* **)**  
  
 **排程 (** *排程種類* **,，** *運算式* **)**  
  
 *排程類型*:  
  
 **靜態**  
  
 **動態**  
  
 **指引**  
  
 **執行階段**  
  
 *區段建構*:  
  
 *sections 指示詞的區段範圍*  
  
 *sections 指示詞*:  
  
 **# pragma omp 章節** *區段子句*optseq *新行*  
  
 *區段子句*:  
  
 *資料子句*  
  
 **nowait**  
  
 *區段範圍*:  
  
 *{區段順序}*  
  
 *區段順序*:  
  
 *區段指示詞*選擇 *結構化的區塊*  
  
 *區段順序區段指示詞結構化的區塊*  
  
 *區段指示詞*:  
  
 **# pragma omp 區段** *新行*  
  
 *單一建構*:  
  
 *單一指示詞結構化的區塊*  
  
 *單一指示詞*:  
  
 **# pragma omp 單一** *單一子句*optseq *新行*  
  
 *單一子句*:  
  
 *資料子句*  
  
 **nowait**  
  
 *平行的建構*:  
  
 *指示詞平行的反覆運算陳述式*  
  
 *平行的指示詞*:  
  
 **# pragma omp 平行的** *平行 for 子句*optseq *新行*  
  
 *平行 for 子句*:  
  
 *唯一平行子句*  
  
 *唯一的子句*  
  
 *資料子句*  
  
 *平行區段建構*:  
  
 *平行 sections 指示詞的區段範圍*  
  
 *平行 sections 指示詞*:  
  
 **# pragma omp 平行章節** *平行區段子句*optseq *新行*  
  
 *平行區段子句*:  
  
 *唯一平行子句*  
  
 *資料子句*  
  
 *主要建構*:  
  
 *master 指示詞結構化的區塊*  
  
 *master 指示詞*:  
  
 **# pragma omp 主要** *新行*  
  
 *critical 建構*:  
  
 *critical 指示詞結構化的區塊*  
  
 *critical 指示詞*:  
  
 **# pragma omp 重大** *區域片語*選擇 *新行*  
  
 *區域片語*:  
  
 *（識別碼）*  
  
 *barrier 指示詞*:  
  
 **# pragma omp 屏障** *新行*  
  
 *atomic 建構*:  
  
 *atomic 指示詞的運算式陳述式*  
  
 *atomic 指示詞*:  
  
 **不可部分完成的 # pragma omp** *新行*  
  
 *flush 指示詞*:  
  
 **# pragma omp 排清** *排清變數*選擇 *新行*  
  
 *排清變數*:  
  
 *（變數清單）*  
  
 *排序建構*:  
  
 *排序指示詞結構化的區塊*  
  
 *排序指示詞*:  
  
 **# pragma omp 排序** *新行*  
  
 *宣告*:  
  
 **/\* 標準的宣告 \*/**  
  
 *threadprivate 指示詞*  
  
 *threadprivate 指示詞*:  
  
 **# pragma omp threadprivate (** *變數清單*  **)** *新行*  
  
 *資料子句*:  
  
 **私用 (** *變數清單* **)**  
  
 **copyprivate (**  *變數清單*  **)**  
  
 **firstprivate (**  *變數清單*  **)**  
  
 **lastprivate (** *變數清單*  **)**  
  
 **共用 (** *變數清單* **)**  
  
 **預設 （共用）**  
  
 **預設 （無）**  
  
 **減少 (**  *減少運算子*  **:**  *變數清單*  **)**  
  
 **copyin (**  *變數清單*  **)**  
  
 *減少運算子*:  
  
 *其中一個*: **+ \* -（& s) ^ & #124; （& s) （& s) （& s) #124; & #124;**  
  
 **/\* 在 C 中 \*/**  
  
 *變數清單*:  
  
 *識別項*  
  
 *變數清單* **,，** *識別碼*  
  
 **/\* 在 c + + \*/**  
  
 *變數清單*:  
  
 *識別碼運算式*  
  
 *變數清單* **,，** *識別碼運算式*