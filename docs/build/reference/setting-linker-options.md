---
title: 設定連結器選項 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- files [C++], LINK
- input files [C++], linker
- linker [C++], ways to set options
- linker [C++], switches
- input files [C++]
- object/library modules
ms.assetid: e08fb487-0f2e-4f24-87db-232dbc8bd2e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2fd99732c7f79b3c61ff5b31516b98a478ed4a8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713072"
---
# <a name="setting-linker-options"></a>設定連結器選項

內部或外部的開發環境，可以設定連結器選項。 每個連結器選項的主題討論如何在開發環境中設定。 請參閱[連結器選項](../../build/reference/linker-options.md)如需完整清單。

當您在開發環境外部執行連結時，您可以指定輸入一或多個方式：

- 在 [命令列](../../build/reference/linker-command-line-syntax.md)

- 使用[命令檔](../../build/reference/link-command-files.md)

- 在 [環境變數](../../build/reference/link-environment-variables.md)

第一個程序選項連結連結環境變數中指定，後面接著在命令列指定的順序和命令檔中的選項。 如果使用不同的引數重複選項時，最後一個處理的優先順序較高。

選項會套用至整個建置;沒有選項可以套用至特定的輸入檔中。

## <a name="see-also"></a>另請參閱

[C/C++ 建置參考](../../build/reference/c-cpp-building-reference.md)<br/>
[連結器選項](../../build/reference/linker-options.md)