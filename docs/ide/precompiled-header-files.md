---
title: 先行編譯標頭檔 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- stdafx.h
dev_langs:
- C++
helpviewer_keywords:
- stdafx.h
- PCH files, file descriptions
- .pch files, file descriptions
- precompiled header files, file descriptions
- stdafx.cpp
ms.assetid: 8228d87a-5609-41f3-9697-b16094c000e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d93486d8df8cdb8bc253a0e71037f4e2ddf9e128
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890475"
---
# <a name="precompiled-header-files"></a>先行編譯標頭檔

這些檔案可用來建置先行編譯標頭檔 *Projname*.pch 和先行編譯類型檔 Stdafx.obj。

這些檔案位於 *Projname* 目錄中。 在方案總管中，Stdafx.h 位於 [標頭檔] 資料夾中，而 Stdafx.cpp 則位於 [原始程式檔] 資料夾中。

|檔案名稱|描述|
|---------------|-----------------|
|stdafx.h|Include 檔，代表常用但不常變更的標準系統 Include 檔和專案特定 Include 檔。<br /><br /> 您不能定義或取消定義 stdafx.h 中的任何 _AFX_NO_XXX 巨集。|
|stdafx.cpp|包含前置處理器指示詞 `#include "stdafx.h"` ，並為先行編譯類型加入 Include 檔。 任何類型的先行編譯檔 (包括標頭檔)，都可藉由限制僅編譯需要的檔案，來加快編譯時間。 第一次建置專案之後，您會發現後續組建的建置時間會加快許多，這是因為先行編譯標頭檔之故。|

## <a name="see-also"></a>請參閱

[為 Visual C++ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[使用專案屬性](../ide/working-with-project-properties.md)