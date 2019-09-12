---
title: 連結器工具錯誤 LNK1352
description: 嘗試進行不支援的區段合併時，會發生連結器工具錯誤 LNK1352。
ms.date: 09/10/2019
f1_keywords:
- LNK1352
helpviewer_keywords:
- LNK1352
ms.openlocfilehash: 38f773bfd669529dfb1ada9c7bb59e6f0962c9c7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908379"
---
# <a name="linker-tools-error-lnk1352"></a>連結器工具錯誤 LNK1352

> '*section_name_1*' 和 '*section_name_2*' 無法合併到不同的區段

## <a name="remarks"></a>備註

連結器偵測到不允許的區段合併，因為*section_name_1*和*section_name_2*必須合併到相同的區段中。 例如，如果連結器偵測到將`.stls`區段`.tls`和區段合併到不同區段的嘗試，就會發生這個錯誤。

### <a name="to-correct-this-error"></a>更正這個錯誤

針對此問題，請在連結器命令列上核取 [ [/merge](../../build/reference/merge-combine-sections.md) ] 選項。

## <a name="see-also"></a>另請參閱

[連結器工具錯誤和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
