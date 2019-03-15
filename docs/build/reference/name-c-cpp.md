---
title: NAME (C/C++)
ms.date: 11/04/2016
f1_keywords:
- name
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
ms.openlocfilehash: d0813befc622db72e095c449794405fc5d58465b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812183"
---
# <a name="name-cc"></a>NAME (C/C++)

指定主要輸出檔的名稱。

```
NAME [application][BASE=address]
```

## <a name="remarks"></a>備註

若要指定輸出檔名稱對等的方法是使用[/out](out-output-file-name.md)連結器選項和設定基底位址的對等方式是使用[基底/](base-base-address.md)連結器選項。 如果同時指定這兩者，/外覆寫**名稱**。

如果您建立 DLL 時，名稱只會影響 DLL 名稱。

## <a name="see-also"></a>另請參閱

[模組定義陳述式的規則](rules-for-module-definition-statements.md)
