---
title: 檔名部分語法
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, filename-parts
- filename-parts syntax in NMAKE
- NMAKE program, syntax
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
ms.openlocfilehash: 159558081fd9884f969ddc66833d927b8569a79b
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417472"
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

- %s will be c:\prog.exe

- %&#124;F will be c:\prog.exe

- %&#124;會 c dF。

- %&#124;pF will be c:\

- %&#124;會 prog fF。

- %&#124;eF 會 exe

## <a name="see-also"></a>另請參閱

[Makefile 中的命令](../build/commands-in-a-makefile.md)
