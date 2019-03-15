---
title: 定義規則
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
ms.openlocfilehash: cd82dc5b0693e563fd3d75a0215265089ff57913
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824979"
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

[在規則中的搜尋路徑](search-paths-in-rules.md)

## <a name="see-also"></a>另請參閱

[推斷規則](inference-rules.md)
