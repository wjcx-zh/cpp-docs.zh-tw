---
title: .Res 檔做為連結器輸入 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- RES files as linker input
- .res files as linker input
- linking [C++], resource files
- resource files, linking
ms.assetid: 9c37ab00-97df-4d9a-91cd-6bf132970683
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a6a572013a29420670a2aef8c91c9c4bc64e871
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706295"
---
# <a name="res-files-as-linker-input"></a>.Res 檔做為連結器輸入

連結程式時，您可以指定一個.res 檔案。 資源編譯器 (版本 RC) 會建立.res 檔案。 連結會自動將.res 檔案轉換成 COFF。 LINK.exe 相同目錄中，或在 PATH 環境變數所指定的目錄中，必須是 CVTRES.exe 工具。

## <a name="see-also"></a>另請參閱

[LINK 輸入檔](../../build/reference/link-input-files.md)<br/>
[連結器選項](../../build/reference/linker-options.md)