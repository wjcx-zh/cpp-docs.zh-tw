---
title: 3.2 鎖定函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0ec855c6-55a9-49d7-bee4-5edae6e86a1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd788b0ef1c72b1f38a44ee608ce0c7760e24adc
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="32-lock-functions"></a>3.2 鎖定函式
本節中所述的函式來操作用於同步處理的鎖定。  
  
 下列函式中，鎖定變數必須具有型別**omp_lock_t**。 透過這些函式時，必須只能存取這個變數。 所有的鎖定函式需要有一個指標指向的引數**omp_lock_t**型別。  
  
-   `omp_init_lock`函式會初始化簡單鎖定。  
  
-   `omp_destroy_lock`函式會移除簡單鎖定。  
  
-   `omp_set_lock`函式會等候直到簡單鎖定可用為止。  
  
-   `omp_unset_lock`函式會釋放簡單鎖定。  
  
-   `omp_test_lock`函式會測試的簡單鎖定。  
  
 下列函式中，鎖定變數必須具有型別**omp_nest_lock_t**。  透過這些函式時，必須只能存取這個變數。 所有可巢狀鎖定函式需要有一個指標指向的引數**omp_nest_lock_t**型別。  
  
-   `omp_init_nest_lock`函式會初始化可巢狀的鎖定。  
  
-   `omp_destroy_nest_lock`函式會移除可巢狀的鎖定。  
  
-   `omp_set_nest_lock`函式會等候直到可巢狀鎖定可用為止。  
  
-   `omp_unset_nest_lock`函式會釋放可巢狀的鎖定。  
  
-   `omp_test_nest_lock`函式會測試可巢狀的鎖定。  
  
 OpenMP 鎖定函式會存取方式它們一律讀取和鎖定變數的最新值更新鎖定變數。 因此，不需要包含明確的 OpenMP 程式**排清**指示詞，可確保在不同執行緒之間一致鎖定變數的值。 (可能會需要**排清**指示詞，可讓其他變數的值一致。)