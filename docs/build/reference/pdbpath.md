---
title: -PDBPATH |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /pdbpath
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, path
- -PDBPATH dumpbin option
- /PDBPATH dumpbin option
- PDBPATH dumpbin option
- PDB files, path
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c9d93ef38ba444fd716bd3363a6605eae66dfec
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699671"
---
# <a name="pdbpath"></a>/PDBPATH

```
/PDBPATH[:VERBOSE] filename
```

### <a name="parameters"></a>參數

*filename*<br/>
您要尋找相符的.pdb 檔案的.dll 或.exe 檔案的名稱。

**： 詳細資訊**<br/>
（選擇性）報告所有的目錄，其中已嘗試找到.pdb 檔案。

## <a name="remarks"></a>備註

/PDBPATH 會搜尋您的電腦相同路徑進行偵錯工具會搜尋.pdb 檔案，並將報告它.pdb 檔如果有的話，對應中指定的檔案*filename*。

在使用 Visual Studio 偵錯工具時，可能會遇到問題，因為，偵錯工具用於不同版本的檔案進行偵錯的.pdb 檔案中。

/PDBPATH 會搜尋.pdb 檔案，依照下列路徑：

- 請檢查可執行檔所在的位置。

- 請檢查 PDB 寫入至可執行檔的位置。 這通常是在映像已連結的位置。

- 檢查 Visual Studio IDE 中設定的搜尋路徑。

- 檢查沿著 _NT_SYMBOL_PATH 和 _NT_ALT_SYMBOL_PATH 路徑環境變數。

- 請檢查 Windows 目錄中。

## <a name="see-also"></a>另請參閱

[DUMPBIN 選項](../../build/reference/dumpbin-options.md)<br/>
[/PDBALTPATH (使用替代 PDB 路徑)](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)