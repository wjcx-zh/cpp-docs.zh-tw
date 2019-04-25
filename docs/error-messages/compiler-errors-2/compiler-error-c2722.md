---
title: 編譯器錯誤 C2722
ms.date: 11/04/2016
f1_keywords:
- C2722
helpviewer_keywords:
- C2722
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
ms.openlocfilehash: 4274ac6ec33e0176f998fcf5a2b3efd570a4009f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383031"
---
# <a name="compiler-error-c2722"></a>編譯器錯誤 C2722

':: 運算子 ': 不合法的下列運算子命令;使用 'operator operator'

`operator`陳述式重新定義`::new`或`::delete`。 `new`並`delete`運算子是全域的因此範圍解析運算子 (`::`) 就沒有意義。 請移除 `::` 運算子。