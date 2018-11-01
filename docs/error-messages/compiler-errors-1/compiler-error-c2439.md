---
title: 編譯器錯誤 C2439
ms.date: 11/04/2016
f1_keywords:
- C2439
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
ms.openlocfilehash: f71112d3f37f3e4d1a4f41bade95726d7aa0a0bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644349"
---
# <a name="compiler-error-c2439"></a>編譯器錯誤 C2439

'identifier': 無法初始化成員

無法初始化類別、 結構或等位成員。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 嘗試初始化間接基底類別或結構。

1. 嘗試初始化的類別或結構繼承的成員。 繼承的成員必須初始化類別或結構的建構函式。