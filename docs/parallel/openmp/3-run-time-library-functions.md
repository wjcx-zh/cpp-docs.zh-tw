---
title: 3. 執行階段程式庫函式
ms.date: 11/04/2016
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: e1d8d498be7f58bcf510025c67c539127f450824
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484093"
---
# <a name="3-run-time-library-functions"></a>3.執行階段程式庫函式

本章節描述 OpenMP C 和 c + + 執行階段程式庫函式。 標頭 **\<omp.h >** 會宣告兩種類型，可用來控制和查詢平行執行環境，並鎖定函式，可用來同步處理資料的存取權的數個函式。

型別**omp_lock_t**是物件類型可代表鎖定可供使用，或執行緒擁有鎖定。 這些鎖定指*簡單鎖定*。

型別**omp_nest_lock_t**是物件類型可代表任一的鎖定，或者這兩個執行緒的識別擁有鎖定並*巢狀計數*（如下所述）。 這些鎖定指*可巢狀鎖定*。

外部"C"連結函式是程式庫函式。

這一章中的說明可分成下列主題：

- 執行環境函式 (請參閱[3.1 節](../../parallel/openmp/3-1-execution-environment-functions.md)上第 35 頁)。

- 鎖定函式 (請參閱[第 3.2 節](../../parallel/openmp/3-2-lock-functions.md)41 頁上)。