---
title: 版本 （C/C + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VERSION
dev_langs:
- C++
helpviewer_keywords:
- VERSION .def file statement
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7330d979e841d952f7e800e52ae762256ede6808
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718298"
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