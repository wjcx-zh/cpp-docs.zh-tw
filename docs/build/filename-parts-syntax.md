---
title: 檔名部分語法 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- syntax, filename-parts
- filename-parts syntax in NMAKE
- NMAKE program, syntax
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5bf7a9685face739059c4b947a5796cc0a28950a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703166"
---
# <a name="filename-parts-syntax"></a>檔名部分語法

在命令中的檔名部分語法表示的第一個相依檔案名稱 （這可能是隱含的相依性） 的元件。 檔名元件檔案的磁碟機、 路徑、 主檔名和延伸模組所指定，不是它存在於磁碟上。 使用 **%s**來代表完整的檔名。 使用 **%&#124;**[*組件*]**F** (分隔號字元後面的百分比符號) 來代表組件的檔名，其中*部分*可以是零個或多個下列的字母，依任何順序。

|字母|描述|
|------------|-----------------|
|任何字母|完整名稱 (與相同 **%s**)|
|**d**|磁碟機|
|**p**|路徑|
|**f**|檔案主檔名|
|**e**|副檔名|

例如，如果檔案名稱是 c:\prog.exe:

- 會 c:\prog.exe %s。

- %&#124;會 c:\prog.exe F。

- %&#124;會 c dF。

- %&#124;pF 會是 c:\

- %&#124;會 prog fF。

- %&#124;eF 會 exe

## <a name="see-also"></a>另請參閱

[Makefile 中的命令](../build/commands-in-a-makefile.md)