---
title: 指定內嵌檔
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, inline files
- inline files [C++], specifying NMAKE
- files [C++], inline
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
ms.openlocfilehash: 7eb123ef3f2115df5c65d266630bded8cb54baae
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826161"
---
# <a name="specifying-an-inline-file"></a>指定內嵌檔

指定兩個角括弧 (<<) 命令中何處*filename*出現。 角括號不可為巨集展開。

## <a name="syntax"></a>語法

```
<<[filename]
```

## <a name="remarks"></a>備註

執行命令時，會取代角括號*filename*，如果指定，或將 NMAKE 產生的唯一名稱。 如果指定， *filename*必須遵循不含空格或定位字元的角括號。允許的路徑。 需要不含副檔名，或假設。 如果*filename*指定的檔案建立在目前或指定的目錄，該名稱的覆寫任何現有的檔案; 否則它會建立在 TMP 目錄 (或目前的目錄中，如果 TMP 環境變數未定義）。 如果先前*filename*是重複使用，NMAKE 會取代先前的檔案。

## <a name="see-also"></a>另請參閱

[Makefile 中的內嵌檔](inline-files-in-a-makefile.md)
