---
title: main 函式限制
ms.date: 11/04/2016
f1_keywords:
- Main
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
ms.openlocfilehash: 9ccea987b05c7854e78ba1621fd6c0a065d73d5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555725"
---
# <a name="main-function-restrictions"></a>main 函式限制

數個限制**主要**並不適用於任何其他 c + + 函式的函式。 **主要**函式：

- 無法多載 (請參閱[函式多載](function-overloading.md))。

- 不可以宣告為**內嵌**。

- 不可以宣告為**靜態**。

- 無法取得自己的位址。

- 不能被呼叫。

## <a name="see-also"></a>另請參閱

[main：程式啟動](../cpp/main-program-startup.md)