---
title: 編譯器錯誤 C3744
ms.date: 11/04/2016
f1_keywords:
- C3744
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
ms.openlocfilehash: 407ed4b30b55b63aa9bf36de9f8675a531d70534
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227099"
---
# <a name="compiler-error-c3744"></a>編譯器錯誤 C3744

__unhook 必須對受控事件至少 3 個引數

[__Unhook](../../cpp/unhook.md)函式必須接受三個參數，用於編譯 Managed Extensions for 程式時C++。

`__hook` 和`__unhook`/clr 程式設計與不相容。 改為使用等號比較運算子 + = 和-= 運算子。

C3744 才可使用過時的編譯器選項 **/clr: oldsyntax**。
