---
title: 編譯器警告 （層級 4） C4057 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4057
dev_langs:
- C++
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b10ce6b67fd24b4b8db01177af0225deab9dba4b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088003"
---
# <a name="compiler-warning-level-4-c4057"></a>編譯器警告 (層級 4) C4057

'operator' : 'identifier1' 在間接取值上與 'identifier2' 的基底類型有些許不同

兩個指標運算式參考不同的基底類型。 運算式使用時沒有轉換。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 混合帶正負號和不帶正負號的類型。

1. 混合了 **short** 和 **long** 類型。