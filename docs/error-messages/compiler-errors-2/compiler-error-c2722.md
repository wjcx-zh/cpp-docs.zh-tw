---
title: 編譯器錯誤 C2722 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2722
dev_langs:
- C++
helpviewer_keywords:
- C2722
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9138172bb108095c4e72407f1e17e8f4fa2370c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082660"
---
# <a name="compiler-error-c2722"></a>編譯器錯誤 C2722

':: 運算子 ': 不合法的下列運算子命令;使用 'operator operator'

`operator`陳述式重新定義`::new`或`::delete`。 `new`並`delete`運算子是全域的因此範圍解析運算子 (`::`) 就沒有意義。 移除`::`運算子。