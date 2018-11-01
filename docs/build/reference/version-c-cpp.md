---
title: VERSION (C/C++)
ms.date: 11/04/2016
f1_keywords:
- VERSION
helpviewer_keywords:
- VERSION .def file statement
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
ms.openlocfilehash: 98758da627390ba4c7e852905457527a343baccc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667372"
---
# <a name="version-cc"></a>VERSION (C/C++)

將數字的.exe 檔案的標頭中的連結或 DLL 會告知。

```
VERSION major[.minor]
```

## <a name="remarks"></a>備註

*主要*並*次要*引數是介於 0 到 65535 的十進位數字。 預設值是版本 0.0。

指定的版本號碼的對等方法是使用[版本資訊](../../build/reference/version-version-information.md)(/ 版本) 選項。

## <a name="see-also"></a>另請參閱

[模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)