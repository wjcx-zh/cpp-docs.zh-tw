---
title: 檔名巨集
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- filename macros in NMAKE
- NMAKE program, filename macros
ms.assetid: 20afd6b3-5b6c-4e33-9d01-309ce98ef9db
ms.openlocfilehash: 2e7552d77d753d4e93734f2fc9a35b3b68d8d55c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457690"
---
# <a name="filename-macros"></a>檔名巨集

檔名巨集是預先定義為相依性 （不是完整的檔名規格在磁碟上） 中指定的檔名。 這些巨集不需要括在括號時叫用;指定只有 $ 如所示。

|巨集|意義|
|-----------|-------------|
|**$\@**|目前的目標完整名稱 （路徑、 主檔名、 延伸模組），如目前所指定。|
|**$$\@**|目前的目標完整名稱 （路徑、 主檔名、 延伸模組），如目前所指定。 有效只能作為相依性中的相依性。|
|**$&#42;**|目前的目標路徑和基底名稱不包含副檔名。|
|**$&#42;&#42;**|目前目標的所有相依項目。|
|**$?**|使用時間戳記晚於目前的目標的所有相依項目。|
|**$<**|相依檔案時間戳記晚於目前的目標。 只有在推斷規則中的命令有效。|

若要指定預先定義的檔案名稱巨集的一部份，附加巨集修飾詞和括號括住的已修改的巨集。

|修飾詞|產生的檔案名稱部分|
|--------------|-----------------------------|
|**D**|磁碟機，再加上目錄|
|**B**|基底名稱|
|**F**|基底名稱再加上擴充功能|
|**R**|磁碟機加上目錄再加上基底名稱|

## <a name="see-also"></a>另請參閱

[特殊的 NMAKE 巨集](../build/special-nmake-macros.md)
