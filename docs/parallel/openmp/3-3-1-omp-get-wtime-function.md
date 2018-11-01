---
title: 3.3.1 omp_get_wtime 函式
ms.date: 11/04/2016
ms.assetid: 90188bd2-c53e-4398-8946-d3ecc92fa0f6
ms.openlocfilehash: 544a1bc9a613a2888cb7c5e68e54fdfae1b1c333
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460563"
---
# <a name="331-ompgetwtime-function"></a>3.3.1 omp_get_wtime 函式

`omp_get_wtime`函式會傳回雙精度浮點數值等於 24 小時制的時鐘時間 （秒），因為某些 「 時間在過去 」。  實際 「 時間在過去 」，不過它保證不會在應用程式執行期間變更。 格式如下：

```
#include <omp.h>
double omp_get_wtime(void);
```

預期的函式，將會用來測量已耗用時間，如下列範例所示：

```
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

傳回的時間都 「 每個執行緒 times"這表示不需要是全域一致的多個參與的應用程式中的所有執行緒。