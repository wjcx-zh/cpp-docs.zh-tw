---
title: Makefile 中的註解 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- makefiles, comments
ms.assetid: 76fd9e3d-5966-47f4-a091-c9e80b232b49
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0bff732a0e9becc9b6c829c70a1bc6701e6031bf
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723946"
---
# <a name="comments-in-a-makefile"></a>Makefile 中的註解

在前面的註解的數字符號 （#）。 NMAKE 會略過下一個新行字元的文字從數字的符號。 例如：

```
# Comment on line by itself
OPTIONS = /MAP  # Comment on macro definition line

all.exe : one.obj two.obj  # Comment on dependency line
    link one.obj two.obj
# Comment in commands block
#   copy *.obj \objects  # Command turned into comment
    copy one.exe \release

.obj.exe:  # Comment on inference rule line
    link $<

my.exe : my.obj ; link my.obj  # Err: cannot comment this
# Error: # must be the first character
.obj.exe: ; link $<  # Error: cannot comment this
```

若要指定常值的數字符號，前面加上插入號 (**^**)，如下：

```
DEF = ^#define  #Macro for a C preprocessing directive
```

## <a name="see-also"></a>另請參閱

[Makefile 內容](../build/contents-of-a-makefile.md)