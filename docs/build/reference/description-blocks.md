---
title: 描述區塊
ms.date: 11/04/2016
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: da9265d6b0026bb47496d3aa58847824b5d634d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293806"
---
# <a name="description-blocks"></a>描述區塊

描述區塊是相依性線條，然後選擇性地執行命令區塊：

```
targets... : dependents...
    commands...
```

相依性一行指定一個或多個目標和零或多個相依項目。 目標必須是該行的開頭。 允許來自相依項目以冒號 （:） 的個別目標; 空格或定位字元。 若要分割線，請使用反斜線 (\) 之後的目標或相依性。 如果目標不存在，都有較早的時間戳記比相依的或為[虛擬目標](pseudotargets.md)，NMAKE 執行的命令。 如果相依的其他位置為目標並不存在或已過期相對於其自己的相依性，NMAKE 就會更新相依之前更新目前的相依性。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

[目標](targets.md)

[相依性](dependents.md)

## <a name="see-also"></a>另請參閱

[NMAKE 參考](nmake-reference.md)
