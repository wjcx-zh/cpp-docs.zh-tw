---
title: 虛設常式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STUB
dev_langs:
- C++
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 151d7b425a7f397a05e3a06e9d94489a0c76f899
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725110"
---
# <a name="stub"></a>STUB

建立虛擬裝置驅動程式 (VxD) 模組定義檔中使用時，可讓您指定檔案名稱包含 （定義於 WINNT IMAGE_DOS_HEADER 結構。H) 要用於虛擬裝置驅動程式 (VxD)，而不是預設標頭。

```
STUB:filename
```

## <a name="remarks"></a>備註

指定的對等方式*檔名*是具有[/虛設常式](../../build/reference/stub-ms-dos-stub-file-name.md)連結器選項。

虛設常式時為有效的模組定義檔中只建置 VxD。

## <a name="see-also"></a>另請參閱

[模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)