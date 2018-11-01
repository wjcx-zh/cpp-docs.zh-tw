---
title: 目標
ms.date: 11/04/2016
helpviewer_keywords:
- targets, specifying in NMAKE
ms.assetid: 826ee849-4278-4c6e-97c3-79a2b5fe6463
ms.openlocfilehash: f2163b6fdbd03c5cc1f5af307b5646f31d8a0c34
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664213"
---
# <a name="targets"></a>目標

在相依性的一行中，指定一或多個目標，使用任何有效的檔名、 目錄名稱，或[虛擬目標](../build/pseudotargets.md)。 使用一或多個空格或定位點分隔多個目標。 目標不區分大小寫。 允許的路徑與檔案名稱。 目標不能超過 256 個字元。 如果冒號之前的目標是單一字元，使用分隔的空間;否則，NMAKE 會解譯為磁碟機代碼字母冒號組合。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

[虛擬目標](../build/pseudotargets.md)

[多個目標](../build/multiple-targets.md)

[累計相依性](../build/cumulative-dependencies.md)

[多重描述區塊中的目標](../build/targets-in-multiple-description-blocks.md)

[相依性的副作用](../build/dependency-side-effects.md)

## <a name="see-also"></a>另請參閱

[描述區塊](../build/description-blocks.md)