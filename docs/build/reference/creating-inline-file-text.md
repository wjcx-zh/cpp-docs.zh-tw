---
title: 建立內嵌檔文字
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
ms.openlocfilehash: a45aa526ca99af93cda86a2a8e0580d4d036ca6d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272317"
---
# <a name="creating-inline-file-text"></a>建立內嵌檔文字

內嵌檔案是暫時的還是永久的。

## <a name="syntax"></a>語法

```
inlinetext
.
.
.
<<[KEEP | NOKEEP]
```

## <a name="remarks"></a>備註

指定*inlinetext*命令之後的第一行上。 標記的結尾使用雙角括弧 (<<) 位於不同行的開頭。 此檔案包含所有*inlinetext*分隔的方括號之前。 *Inlinetext*可以有巨集展開和替代項目，但不是指示詞或 makefile 註解。 空格、 tab 鍵和新行字元會解譯為常值處理。

暫存檔案存在於工作階段期間，其他命令可以重複使用。 指定**保留**之後右角括號，保留檔案，NMAKE 工作階段中; 之後未命名的檔案會保留在產生的檔名的磁碟上。 指定**NOKEEP**或任何項目為暫存檔。 **保持**並**NOKEEP**不區分大小寫。

## <a name="see-also"></a>另請參閱

[Makefile 中的內嵌檔](inline-files-in-a-makefile.md)
