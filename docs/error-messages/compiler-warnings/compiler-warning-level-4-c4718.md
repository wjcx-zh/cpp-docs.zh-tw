---
title: 編譯器警告 (層級 4) C4718
ms.date: 11/04/2016
f1_keywords:
- C4718
helpviewer_keywords:
- C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
ms.openlocfilehash: c313e26af5f5b17db9c7d001a705ff7211461c2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573670"
---
# <a name="compiler-warning-level-4-c4718"></a>編譯器警告 (層級 4) C4718

'function call': 遞迴呼叫沒有副作用，正在刪除

函式包含遞迴呼叫，但沒有副作用。 正在刪除對此函式的呼叫。 程式的正確性不受影響，但行為受影響。 因為保留呼叫可能會導致執行階段堆疊溢位的例外狀況，所以刪除該呼叫以排除這個可能性。