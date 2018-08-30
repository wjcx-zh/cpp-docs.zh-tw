---
title: 編譯器警告 （層級 1） C4612 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4612
dev_langs:
- C++
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10a0a5640386f5e5673f39d6c2c76ee18fcc7ba7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210726"
---
# <a name="compiler-warning-level-1-c4612"></a>編譯器警告 (層級 1) C4612

> Include 檔檔名錯誤

## <a name="remarks"></a>備註

當檔案名稱不正確或遺漏時， **#pragma include_alias** 會發生這個錯誤。

引數 **#pragma include_alias**陳述式可以使用引號形式 (「*檔名*") 或角括弧形式 (\<*filename*>)，但兩者都必須使用相同的格式。

## <a name="example"></a>範例

```cpp
// C4612.cpp
// compile with: /W1 /LD
#pragma include_alias("StandardIO", <stdio.h>) // C4612
```