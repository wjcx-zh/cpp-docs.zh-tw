---
title: NMAKE 嚴重錯誤 U1035 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1035
dev_langs:
- C++
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0383bf4742d637d669070efa5370ebda0c7ab159
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019857"
---
# <a name="nmake-fatal-error-u1035"></a>NMAKE 嚴重錯誤 U1035

語法錯誤： 必須是 ':' 或 '=' 分隔符號

冒號 (**:**) 或等號 (**=**) 所預期。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 冒號未遵循為目標。

1. 冒號且不得包含空格 （例如，a:） 後面接著單一字母的目標。 NMAKE 解譯它做為磁碟機規格。

1. 冒號未遵循推斷規則。

1. 巨集定義後面沒有等號。

1. 字元後面接著反斜線 (**\\**)，用來繼續執行至新的一行命令。

1. 在出現未遵循任何 NMAKE 語法規則的字串。

1. 文書處理器來格式化的 makefile。