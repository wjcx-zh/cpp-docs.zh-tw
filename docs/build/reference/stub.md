---
title: STUB
ms.date: 11/04/2016
f1_keywords:
- STUB
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
ms.openlocfilehash: fd2e7c4a3bd9fa09b88f4c3caa9b7d5b73c1ad98
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412935"
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
