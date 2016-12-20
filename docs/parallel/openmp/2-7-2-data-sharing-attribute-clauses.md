---
title: "2.7.2 Data-Sharing Attribute Clauses | Microsoft Docs"
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
ms.assetid: 47347d3c-18bd-441f-99cf-7737564c417f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2 Data-Sharing Attribute Clauses
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

數個指示詞會接受子句，讓使用者控制共用的屬性的變數之區域的持續期間。  共用屬性子句只適用於此子句會出現指示詞的語彙範圍內的變數。  並非所有的以下子句允許所有的指示詞。  指示詞將說明在特定的指示詞有效的子句的清單。  
  
 如果變數就會看到平行或發生工作共用的建構，而且未共用的屬性子句中指定變數或 **threadprivate** 指示詞，然後變數共用的。  在平行區域的動態範圍內宣告靜態變數被共用。  堆積配置的記憶體 \(例如，使用 **malloc \(\)** c 或 C\+\+ 或**新** C\+\+ 中的運算子\) 共用。  \(指標以這種記憶體，但是，可以是私用或共用。\) 自動存放工期的任務在平行區域的動態範圍內宣告的變數是私用的。  
  
 大部分的子句接受*變數清單*引數是逗點分隔的清單會顯示的變數。  中參考的變數資料共用子句屬性有型別衍生自範本時，有沒有其他程式中的該變數的參考，這個行為未定義。  
  
 在指示詞的子句中出現的所有變數都必須都是可見的。  可能會重複出現的子句，如有需要，但可能會在多個子句中，指定任何變數，不同之處在於您可以指定變數，在這兩 **firstprivate** 和 **lastprivate** 子句。  
  
 下列章節將說明資料共享的屬性子句：  
  
-   **私用**， [一節 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) 在 25\] 頁面上。  
  
-   **firstprivate**， [一節 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md) 在 26\] 頁面上。  
  
-   **lastprivate**， [一節 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) 在 27\] 頁面上。  
  
-   **共用**， [一節 2.7.2.4](../../parallel/openmp/2-7-2-4-shared.md) 在 27\] 頁面上。  
  
-   **預設**， [一節 2.7.2.5](../../parallel/openmp/2-7-2-5-default.md) 第 28 頁上。  
  
-   **降低**， [一節 2.7.2.6](../../parallel/openmp/2-7-2-6-reduction.md) 第 28 頁上。  
  
-   **copyin**， [一節 2.7.2.7](../../parallel/openmp/2-7-2-7-copyin.md) 在 31\] 頁面上。  
  
-   **copyprivate**， [一節 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) 在 32\] 頁面上。