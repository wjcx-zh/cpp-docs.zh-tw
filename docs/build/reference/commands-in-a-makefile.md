---
title: Makefile 中的命令
ms.date: 11/04/2016
helpviewer_keywords:
- commands, makefiles
ms.assetid: 8085517e-42f4-493b-b8f8-44311fc08c64
ms.openlocfilehash: fcb8737070931cf95d7bfb3971a84e22c7ad70a4
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824729"
---
# <a name="commands-in-a-makefile"></a>Makefile 中的命令

描述區塊或推斷規則指定的命令，以執行相依性已過時的區塊。 NMAKE 會顯示每個命令之前執行，除非 /S， **。無訊息**， **！CMDSWITCHES**，或\@用。 如果描述區塊後面沒有命令區塊，NMAKE 會尋找相符的推斷規則。

命令區塊包含一個或多個命令，每個的那一行。 之間的相依性或規則，並在命令區塊可以不出現任何空白列。 不過，包含只有空格或定位點的資料行可以顯示;這一行會解譯為 null 的命令，並不會發生錯誤。 命令列之間不允許有空白的行。

命令列開始使用一或多個空格或定位點。 反斜線 (\) 後面接著新行字元會解譯為命令中的空間使用線條結尾的反斜線，繼續到下一行的命令。 NMAKE 會解譯為常值反斜線如果任何其他字元，包括空格或索引標籤上，在反斜線。

命令加上分號 （;） 可能會出現在相依性線條或推斷規則，不論是否遵循命令區塊：

```
project.obj : project.c project.h ; cl /c project.c
```

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

[命令修飾詞](command-modifiers.md)

[檔名部分語法](filename-parts-syntax.md)

[Makefile 中的內嵌檔](inline-files-in-a-makefile.md)

## <a name="see-also"></a>另請參閱

[NMAKE 參考](nmake-reference.md)
