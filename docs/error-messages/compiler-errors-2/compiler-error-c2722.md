---
title: 編譯器錯誤 C2722
ms.date: 11/04/2016
f1_keywords:
- C2722
helpviewer_keywords:
- C2722
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
ms.openlocfilehash: 7426df1970dee58cd4363ee345e2286165e375b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202164"
---
# <a name="compiler-error-c2722"></a>編譯器錯誤 C2722

'：： operator '：下列運算子命令不合法;使用 ' operator operator '

`operator` 語句會重新定義 `::new` 或 `::delete`。 `new` 和 `delete` 運算子是全域的，因此範圍解析運算子（`::`）沒有意義。 請移除 `::` 運算子。
