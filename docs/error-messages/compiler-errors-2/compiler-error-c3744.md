---
title: 編譯器錯誤 C3744
ms.date: 11/04/2016
f1_keywords:
- C3744
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
ms.openlocfilehash: 407ed4b30b55b63aa9bf36de9f8675a531d70534
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516229"
---
# <a name="compiler-error-c3744"></a>編譯器錯誤 C3744

__unhook 必須對受控事件至少 3 個引數

[__Unhook](../../cpp/unhook.md)函式必須接受編譯 Managed Extensions for c + + 程式中使用時的三個參數。

`__hook` 和`__unhook`/clr 程式設計與不相容。 改為使用等號比較運算子 + = 和-= 運算子。

C3744 才可使用過時的編譯器選項 **/clr: oldsyntax**。
