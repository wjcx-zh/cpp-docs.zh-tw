---
title: NMAKE 嚴重錯誤 U1070 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1070
dev_langs:
- C++
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6eb462e5c3c7e497cde55151bf92c62ffb2afcd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087015"
---
# <a name="nmake-fatal-error-u1070"></a>NMAKE 嚴重錯誤 U1070

在巨集定義 'macroname' 循環

指定的巨集定義包含巨集，其定義包含指定的巨集。 循環的巨集的定義是無效的。

## <a name="example"></a>範例

下列巨集定義

```
ONE=$(TWO)
TWO=$(ONE)
```

會導致下列錯誤：

```
cycle in macro definition 'TWO'
```