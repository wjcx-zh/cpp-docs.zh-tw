---
title: 編譯器錯誤 C3180
ms.date: 11/04/2016
f1_keywords:
- C3180
helpviewer_keywords:
- C3180
ms.assetid: 5281f583-7df7-418a-8507-d4da67ed6572
ms.openlocfilehash: bfe2699ce448aa879f0c93aa431a17dbc1334274
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662029"
---
# <a name="compiler-error-c3180"></a>編譯器錯誤 C3180

'type name': 名稱超過中繼資料 'limit' 個字元的限制

編譯器會截斷在中繼資料中的 managed 類型的名稱。 截斷會造成類型無法使用`#using`指示詞 （或另一種語言的對等項目）。

類型名稱限制包含任何命名空間限定性條件。