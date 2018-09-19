---
title: 編譯器警告 （層級 1） C4041 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4041
dev_langs:
- C++
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ff2c8066557e420ecd7de561d7731b7be733315
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085780"
---
# <a name="compiler-warning-level-1-c4041"></a>編譯器警告 (層級 1) C4041

編譯器限制 : 瀏覽器資訊超出編譯器上限，已終止輸出

瀏覽器資訊超過編譯器限制。

這個警告可能是使用 [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (包含區域變數的瀏覽器資訊) 進行編譯所造成。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 使用 /Fr (未含區域變數的瀏覽器資訊) 進行編譯。

1. 停用瀏覽器輸出 (不使用 /FR 或 /Fr 進行編譯)。