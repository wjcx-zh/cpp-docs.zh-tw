---
title: "2.7.2 資料共用屬性子句 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 47347d3c-18bd-441f-99cf-7737564c417f
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c63ece0feea0426fffbafa600f578e342e85fc2c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="272-data-sharing-attribute-clauses"></a>2.7.2 資料共用屬性子句
數個指示詞會接受子句可讓使用者控制共用的變數屬性區域的持續時間。 共用屬性子句僅適用於中的指示詞子句會出現語彙範圍的變數。 並非所有的下列子句允許所有指示詞。 指示詞將詳述的特定指示詞為有效的子句清單。  
  
 如果變數是平行時顯示或發生工作共用建構，且會共用屬性子句中未指定變數或**threadprivate**指示詞，然後變數共用的。 在平行區域的動態範圍內宣告的靜態變數會共用。 堆積配置的記憶體 (例如，使用**malloc （)** C 或 c + + 或**新**運算子在 c + +) 共用。 （指標給這個記憶體，不過，可以是私人或共用。）具有自動儲存期，在平行區域的動態範圍內宣告的變數都是私用。  
  
 子句中的大部分接受*變數清單*引數，這是所顯示變數的逗號分隔清單。 如果變數參考中的資料共用屬性子句具有型別衍生自範本，而且有沒有其他參考該變數在程式中，行為是未定義。  
  
 指示詞子句中出現的所有變數都必須都是可見的。 子句可能會重複，如有需要但沒有任何變數可指定在多個子句中，不同之處在於變數可以指定在**firstprivate**和**lastprivate**子句。  
  
 下列章節說明的資料共用屬性子句：  
  
-   **私用**，[區段 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md)在 25 頁面上。  
  
-   **firstprivate**，[區段 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md) 26 頁面上。  
  
-   **lastprivate**，[區段 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) 27 頁面上。  
  
-   **共用**，[區段 2.7.2.4](../../parallel/openmp/2-7-2-4-shared.md) 27 頁面上。  
  
-   **預設**，[區段 2.7.2.5](../../parallel/openmp/2-7-2-5-default.md)在 28 頁面上。  
  
-   **減少**，[區段 2.7.2.6](../../parallel/openmp/2-7-2-6-reduction.md)在 28 頁面上。  
  
-   **copyin**，[區段 2.7.2.7](../../parallel/openmp/2-7-2-7-copyin.md) 31 頁面上。  
  
-   **copyprivate**，[區段 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) 32 頁面上。