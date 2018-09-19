---
title: 嚴重錯誤 C1002 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1002
dev_langs:
- C++
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82f08255484b11f9f5d87fb67ac8ac7b401d4f6e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044141"
---
# <a name="fatal-error-c1002"></a>嚴重錯誤 C1002

編譯器於第二編譯階段堆積空間不足

在其第二個階段，可能是因為太多符號或複雜運算式的程式編譯器動態記憶體空間不足。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 您可以將原始程式檔分成數個較小的檔案。

1. 分成較小的子運算式的運算式。

1. 移除其他程式或驅動程式所耗用的記憶體。