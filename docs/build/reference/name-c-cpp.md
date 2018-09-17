---
title: 名稱 （C/C + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- name
dev_langs:
- C++
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc37a96e50c6cd5bae2cc60661db04f3b92d162b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715750"
---
# <a name="name-cc"></a>NAME (C/C++)

指定主要輸出檔的名稱。

```
NAME [application][BASE=address]
```

## <a name="remarks"></a>備註

若要指定輸出檔名稱對等的方法是使用[/out](../../build/reference/out-output-file-name.md)連結器選項和設定基底位址的對等方式是使用[基底/](../../build/reference/base-base-address.md)連結器選項。 如果同時指定這兩者，/外覆寫**名稱**。

如果您建立 DLL 時，名稱只會影響 DLL 名稱。

## <a name="see-also"></a>另請參閱

[模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)