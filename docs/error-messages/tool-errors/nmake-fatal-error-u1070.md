---
title: NMAKE 嚴重錯誤 U1070
ms.date: 11/04/2016
f1_keywords:
- U1070
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
ms.openlocfilehash: 008d49df3460cb7cf760e4b278db20da444555fe
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182769"
---
# <a name="nmake-fatal-error-u1070"></a>NMAKE 嚴重錯誤 U1070

巨集定義 ' macroname ' 中的迴圈

給定的巨集定義包含一個宏，其定義包含指定的宏。 迴圈巨集定義無效。

## <a name="example"></a>範例

下列巨集定義

```
ONE=$(TWO)
TWO=$(ONE)
```

造成下列錯誤：

```
cycle in macro definition 'TWO'
```
