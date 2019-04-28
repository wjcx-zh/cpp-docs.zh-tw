---
title: 目標
ms.date: 11/04/2016
helpviewer_keywords:
- targets, specifying in NMAKE
ms.assetid: 826ee849-4278-4c6e-97c3-79a2b5fe6463
ms.openlocfilehash: 52b2f3293b97955b605e2821102247f506c2950b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317649"
---
# <a name="targets"></a>目標

在相依性的一行中，指定一或多個目標，使用任何有效的檔名、 目錄名稱，或[虛擬目標](pseudotargets.md)。 使用一或多個空格或定位點分隔多個目標。 目標不區分大小寫。 允許的路徑與檔案名稱。 目標不能超過 256 個字元。 如果冒號之前的目標是單一字元，使用分隔的空間;否則，NMAKE 會解譯為磁碟機代碼字母冒號組合。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

[虛擬目標](pseudotargets.md)

[多個目標](multiple-targets.md)

[累計相依性](cumulative-dependencies.md)

[多重描述區塊中的目標](targets-in-multiple-description-blocks.md)

[相依性的副作用](dependency-side-effects.md)

## <a name="see-also"></a>另請參閱

[描述區塊](description-blocks.md)