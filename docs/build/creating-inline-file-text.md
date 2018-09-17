---
title: 建立內嵌檔文字 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce0a345c6c2f48d3d5c2e6fb9d9cfc2a5c03e4ed
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720911"
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

指定*inlinetext*命令之後的第一行上。 在不同行的開頭使用雙角括弧 (<<) 標記結尾。 此檔案包含所有*inlinetext*分隔的方括號之前。 *Inlinetext*可以有巨集展開和替代項目，但不是指示詞或 makefile 註解。 空格、 tab 鍵和新行字元會解譯為常值處理。

暫存檔案存在於工作階段期間，其他命令可以重複使用。 指定**保留**之後右角括號，保留檔案，NMAKE 工作階段中; 之後未命名的檔案會保留在產生的檔名的磁碟上。 指定**NOKEEP**或任何項目為暫存檔。 **保持**並**NOKEEP**不區分大小寫。

## <a name="see-also"></a>另請參閱

[Makefile 中的內嵌檔](../build/inline-files-in-a-makefile.md)