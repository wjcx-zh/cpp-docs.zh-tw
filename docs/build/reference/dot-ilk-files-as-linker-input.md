---
title: .Ilk 檔做為連結器輸入 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3b8de3758daf59a543cdcc9f3b73e1d6c6f0ce8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720586"
---
# <a name="ilk-files-as-linker-input"></a>.Ilk 檔做為連結器輸入

當以累加方式連結，連結就會更新.ilk 狀態檔案的第一個的累加連結時所建立。 此檔案具有相同的基底名稱為.exe 檔或.dll 檔案，而且具有副檔名.ilk。 在後續累加連結，連結會更新的.ilk 檔。 .Ilk 檔案遺漏時，連結會執行完整連結，並建立新的.ilk 檔。 如果無法使用的.ilk 檔，連結就會執行非累加連結。 如需有關累加連結的詳細資訊，請參閱 <<c0> [ 以累加方式連結 (/incremental)](../../build/reference/incremental-link-incrementally.md)選項。

## <a name="see-also"></a>另請參閱

[LINK 輸入檔](../../build/reference/link-input-files.md)<br/>
[連結器選項](../../build/reference/linker-options.md)