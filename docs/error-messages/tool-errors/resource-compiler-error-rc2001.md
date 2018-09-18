---
title: 資源編譯器錯誤 RC2001 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2001
dev_langs:
- C++
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d75d0f906ba0d7be75ca5177bc1f58bccd226251
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039968"
---
# <a name="resource-compiler-error-rc2001"></a>資源編譯器錯誤 RC2001

常數中的新行

字串常數，已繼續但沒有第二行的反斜線 (**\\**) 或餘額和期末雙引號 (**"**)。

若要中斷位於原始程式檔中的兩行的字串常數，執行下列其中一項動作：

- 最後第一行的行接續字元、 反斜線。

- 關閉第一列中利用雙引號字串並開啟下一行上的字串，加上另一個單引號。

不足結束 \n，字串常數中內嵌新行字元的逸出序列的第一行。