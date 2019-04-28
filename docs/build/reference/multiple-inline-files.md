---
title: 多重內嵌檔
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
ms.openlocfilehash: 71f17ff6717e717693facb21b4a4341a040b14c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320587"
---
# <a name="multiple-inline-files"></a>多重內嵌檔

命令可以建立多個內嵌檔案。

## <a name="syntax"></a>語法

```
command << <<
inlinetext
<<[KEEP | NOKEEP]
inlinetext
<<[KEEP | NOKEEP]
```

## <a name="remarks"></a>備註

針對每個檔案，指定一或多行的內嵌文字，後面接著包含分隔符號的結尾行。 開始在第一個檔案的分隔列下一行的第二個檔案的文字。

## <a name="see-also"></a>另請參閱

[Makefile 中的內嵌檔](inline-files-in-a-makefile.md)
