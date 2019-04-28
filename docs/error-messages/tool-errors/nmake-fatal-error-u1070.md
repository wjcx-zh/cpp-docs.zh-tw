---
title: NMAKE 嚴重錯誤 U1070
ms.date: 11/04/2016
f1_keywords:
- U1070
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
ms.openlocfilehash: 35bea47f6626dfe283a537d3d96340921c37f3f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367235"
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