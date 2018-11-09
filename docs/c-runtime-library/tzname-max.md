---
title: TZNAME_MAX
ms.date: 10/22/2018
f1_keywords:
- TZNAME_MAX
helpviewer_keywords:
- TZNAME_MAX constant
ms.assetid: e2286cb8-751d-4557-9650-5c4b98a8f7be
ms.openlocfilehash: 1d55f88717613b735cbfd04c5790f05544e1d4c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547910"
---
# <a name="tznamemax"></a>TZNAME_MAX

**已淘汰**。 時區名稱變數允許的字串長度上限。 這個巨集在 Visual Studio 2012 和較舊版本中以 \<limits.h> 定義。 Visual Studio 2013 和更新版本未加以定義。 若要取得保留目前時區名稱所需的長度，請使用 [_get_tzname](../c-runtime-library/reference/get-tzname.md)。

## <a name="syntax"></a>語法

```
#include <limits.h>
```

## <a name="see-also"></a>請參閱

[環境常數](../c-runtime-library/environmental-constants.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)<br/>
[_get_tzname](../c-runtime-library/reference/get-tzname.md)
