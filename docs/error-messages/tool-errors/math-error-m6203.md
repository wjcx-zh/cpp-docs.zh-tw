---
title: 運算錯誤 M6203
ms.date: 11/04/2016
f1_keywords:
- M6203
helpviewer_keywords:
- M6203
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
ms.openlocfilehash: 4433a024d461ee1bc43aa5fa82344190377243b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431131"
---
# <a name="math-error-m6203"></a>運算錯誤 M6203

'function': _OVERFLOW 錯誤

指定的函式的結果就是太大，無法呈現。

這個錯誤呼叫`_matherr`函式名稱、 其引數，與錯誤類型的函式。 您可以重新撰寫`_matherr`函式來自訂特定執行階段浮點數學錯誤的處理。