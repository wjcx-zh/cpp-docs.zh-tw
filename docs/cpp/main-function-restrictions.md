---
title: main 函式限制
ms.date: 11/04/2016
f1_keywords:
- Main
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
ms.openlocfilehash: 9ccea987b05c7854e78ba1621fd6c0a065d73d5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301834"
---
# <a name="main-function-restrictions"></a>main 函式限制

數個限制**主要**不適用於任何其他的函式C++函式。 **主要**函式：

- 無法多載 (請參閱[函式多載](function-overloading.md))。

- 不可以宣告為**內嵌**。

- 不可以宣告為**靜態**。

- 無法取得自己的位址。

- 不能被呼叫。

## <a name="see-also"></a>另請參閱

[主要：程式啟動](../cpp/main-program-startup.md)