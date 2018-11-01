---
title: 編譯器警告 C4962
ms.date: 11/04/2016
f1_keywords:
- C4962
helpviewer_keywords:
- C4962
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
ms.openlocfilehash: e3f7b715da3774d8289fdd526cf1fa0b5bdddba6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585311"
---
# <a name="compiler-warning-c4962"></a>編譯器警告 C4962

'function': 特性指引最佳化已停用，因為最佳化導致分析資料變成不一致

函式並不是使用 /LTCG:PGO 進行編譯，因為函式的計數 (分析) 資料不可靠。 請重做分析，以重新產生包含該函式不可靠分析資料的 .pgc 檔。

此警告預設為關閉。 如需詳細資訊，請參閱 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。