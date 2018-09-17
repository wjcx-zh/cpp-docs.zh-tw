---
title: 定義規則 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8a5cb7a0285f7abf8bcf476141451eae1b10f85
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705571"
---
# <a name="defining-a-rule"></a>定義規則

*Fromext*代表延伸模組的相依檔案，並*toext*代表目標檔案的副檔名。

```
.fromext.toext:
   commands
```

## <a name="remarks"></a>備註

延伸模組不區分大小寫。 可以叫用巨集來代表*fromext*並*toext*; 巨集展開期間前置處理。 句號 （.） 上述*fromext*必須出現在一行的開頭。 前面的冒號 （:） 是由零或多個空格或定位字元。 它可運用只由空格或定位點、 分號 （;），指定的命令、 指定註解，數字符號 （#） 或新行字元。 不允許使用任何其他空格。 命令會指定如描述區塊所示。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

[在規則中的搜尋路徑](../build/search-paths-in-rules.md)

## <a name="see-also"></a>另請參閱

[推斷規則](../build/inference-rules.md)