---
title: 嚴重錯誤 C1002
ms.date: 11/04/2016
f1_keywords:
- C1002
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
ms.openlocfilehash: 78edf886f34665f996497abe323a0ea5d3800c2d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204928"
---
# <a name="fatal-error-c1002"></a>嚴重錯誤 C1002

編譯器於第二編譯階段堆積空間不足

編譯器在第二次行程期間用盡了動態記憶體空間，可能是因為有太多符號或複雜運算式的程式所造成。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 將來源檔案分割成數個較小的檔案。

1. 將運算式分解成較小的子運算式。

1. 移除其他耗用記憶體的程式或驅動程式。
