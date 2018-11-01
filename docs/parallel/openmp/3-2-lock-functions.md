---
title: 3.2 鎖定函式
ms.date: 11/04/2016
ms.assetid: 0ec855c6-55a9-49d7-bee4-5edae6e86a1b
ms.openlocfilehash: c189ba5b1f0bb365b387b4b4b887cfdb74d1bf2c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573065"
---
# <a name="32-lock-functions"></a>3.2 鎖定函式

這一節所述的函式來處理用於同步處理的鎖定。

下列函式中，鎖定變數必須具有型別**omp_lock_t**。 透過這些函式時，必須只能存取此變數。 所有的鎖定函式需要有一個指標指向引數**omp_lock_t**型別。

- `omp_init_lock`函式會初始化簡單的鎖定。

- `omp_destroy_lock`函式會移除簡單的鎖定。

- `omp_set_lock`函式會等候直到有簡單的鎖定可用為止。

- `omp_unset_lock`函式會釋放簡單的鎖定。

- `omp_test_lock`函式會測試簡單的鎖定。

下列函式中，鎖定變數必須具有型別**omp_nest_lock_t**。  透過這些函式時，必須只能存取此變數。 所有可巢狀鎖定函式需要有一個指標指向引數**omp_nest_lock_t**型別。

- `omp_init_nest_lock`函式會初始化可巢狀鎖定。

- `omp_destroy_nest_lock`函式會移除可巢狀鎖定。

- `omp_set_nest_lock`函式會等候，直到可巢狀鎖定可用為止。

- `omp_unset_nest_lock`函式會釋放可巢狀鎖定。

- `omp_test_nest_lock`函式會測試可巢狀鎖定。

OpenMP 鎖定函式會存取鎖定變數的方式表示它們一律在閱讀，並更新鎖定變數的最新的值。 因此，不需要包含明確的 OpenMP 程式**排清**指示詞，以確保鎖定變數的值是在不同執行緒之間一致。 (可能需要**排清**指示詞，以便其他變數的值一致。)