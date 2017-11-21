---
title: "C.2 規則 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 4d52fef7-3eb7-4480-a335-8ed48681092b
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0f0b9c7a74c74f014c9ce8e3873635786fe1e560
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="c2-rules"></a>C.2 規則
標記法節將說明 6.1 C 標準。 此文法附錄顯示 OpenMP C 和 c + + 的指示詞的基本語言文法的延伸模組。  
  
 **/\*在 c + + (ISO/IEC 14882:1998)\*/**  
  
 *陳述式 seq*:  
  
 *statement*  
  
 *openmp 指示詞*  
  
 *陳述式 seq 陳述式*  
  
 *陳述式 seq openmp 指示詞*  
  
 **/\*在 C90 (ISO/IEC 9899: 1990)\*/**  
  
 *statement-list*:  
  
 *statement*  
  
 *openmp 指示詞*  
  
 *statement-list statement*  
  
 *陳述式清單 openmp 指示詞*  
  
 **/\*在 C99 (ISO/IEC 9899: 1999)\*/**  
  
 *區塊項目*:  
  
 *declaration*  
  
 *statement*  
  
 *openmp 指示詞*  
  
 *statement*:  
  
 **/\*標準陳述式\*/**  
  
 *openmp 建構*  
  
 *openmp 建構*:  
  
 *平行建構*  
  
 *建構*  
  
 *區段建構*  
  
 *單一建構*  
  
 *平行的建構*  
  
 *平行區段建構*  
  
 *主要 construc*  
  
 *critical 建構*  
  
 *atomic 建構*  
  
 *ordered 建構*  
  
 *openmp 指示詞*:  
  
 *barrier 指示詞*  
  
 *排清指示詞*  
  
 *結構化區塊*:  
  
 *statement*  
  
 *平行建構*:  
  
 *平行指示詞結構化區塊*  
  
 *平行指示詞*:  
  
 **# pragma omp parallel***平行子句*optseq*新行*   
  
 *平行子句*:  
  
 *唯一平行子句*  
  
 *data 子句*  
  
 *唯一平行子句*:  
  
 **如果 (** *運算式* **)**  
  
 **num_threads (** *運算式* **)**  
  
 *用於建構*:  
  
 *指示詞的反覆運算陳述式*  
  
 *指示詞的*:  
  
 **# pragma omp 如** *for 子句*optseq*新行*  
  
 *for 子句*:  
  
 *唯一 for 子句*  
  
 *data 子句*  
  
 **nowait**  
  
 *唯一 for 子句*:  
  
 **排序**  
  
 **排程 (** *排程種類* **)**  
  
 **排程 (** *排程種類* **，** *運算式* **)**  
  
 *排程種類*:  
  
 **static**  
  
 **dynamic**  
  
 **指引**  
  
 **執行階段**  
  
 *區段建構*:  
  
 *區段指示詞區段範圍*  
  
 *區段指示詞*:  
  
 **# pragma omp 區段***區段子句*optseq*新行*  
  
 *區段子句*:  
  
 *data 子句*  
  
 **nowait**  
  
 *區段範圍*:  
  
 *{區段順序}*  
  
 *區段順序*:  
  
 *區段指示詞*選擇*結構化區塊*  
  
 *區段順序區段指示詞結構化區塊*  
  
 *區段指示詞*:  
  
 **# pragma omp 區段***新行*  
  
 *單一建構*:  
  
 *單一指示詞結構化區塊*  
  
 *單一指示詞*:  
  
 **# pragma omp 單一***單一子句*optseq*新行*  
  
 *單一子句*:  
  
 *data 子句*  
  
 **nowait**  
  
 *平行的建構*:  
  
 *平行指示詞的反覆運算陳述式*  
  
 *平行的指示詞*:  
  
 **# pragma omp parallel for** *平行 for 子句*optseq*新行*  
  
 *for 子句平行*:  
  
 *唯一平行子句*  
  
 *唯一 for 子句*  
  
 *data 子句*  
  
 *平行區段建構*:  
  
 *平行 sections 指示詞區段範圍*  
  
 *平行 sections 指示詞*:  
  
 **# pragma omp parallel 區段***平行區段子句*optseq*新行*  
  
 *平行區段子句*:  
  
 *唯一平行子句*  
  
 *data 子句*  
  
 *master 建構*:  
  
 *主要指示詞結構化區塊*  
  
 *主要指示詞*:  
  
 **# pragma omp master** *新行*  
  
 *critical 建構*:  
  
 *critical 指示詞結構化區塊*  
  
 *critical 指示詞*:  
  
 **# pragma omp 重大***區域片語*選擇*新行*  
  
 *區域片語*:  
  
 *（識別碼）*  
  
 *barrier 指示詞*:  
  
 **# pragma omp 屏障***新行*  
  
 *atomic 建構*:  
  
 *不可部分完成指示詞的運算式陳述式*  
  
 *不可部分完成指示詞*:  
  
 **# pragma omp atomic** *新行*  
  
 *排清指示詞*:  
  
 **# pragma omp 排清***排清變數*選擇*新行*  
  
 *排清變數*:  
  
 *（變數清單）*  
  
 *排序建構*:  
  
 *排序指示詞結構化區塊*  
  
 *排序指示詞*:  
  
 **# pragma omp 排序***新行*  
  
 *宣告*:  
  
 **/\*標準的宣告\*/**  
  
 *threadprivate 指示詞*  
  
 *threadprivate 指示詞*:  
  
 **# pragma omp threadprivate (** *變數清單***)** *新行*   
  
 *data 子句*:  
  
 **私用 (** *變數清單* **)**  
  
 **copyprivate (***變數清單***)**   
  
 **firstprivate (***變數清單***)**   
  
 **lastprivate (** *變數清單***)**   
  
 **共用 (** *變數清單* **)**  
  
 **預設 （共用）**  
  
 **預設 （無）**  
  
 **減少 (***削減運算子***:***變數清單***)**   
  
 **copyin (***變數清單***)**   
  
 *削減運算子*:  
  
 *其中一個*:  **+  \* -（& s) ^ （& s) #124; （& s) （& s) （& s) #124; &#124;**  
  
 **/\*在 C 中\*/**  
  
 *變數清單*:  
  
 *identifier*  
  
 *變數清單* **，** *識別碼*  
  
 **/\*在 c + +\*/**  
  
 *變數清單*:  
  
 *識別碼運算式*  
  
 *變數清單* **，** *識別碼運算式*