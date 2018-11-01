---
title: 編譯器錯誤 C2708
ms.date: 11/04/2016
f1_keywords:
- C2708
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
ms.openlocfilehash: a128613cabb201142c29b833959924dbf8a6e0ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460069"
---
# <a name="compiler-error-c2708"></a>編譯器錯誤 C2708

'identifier': 實質參數長度 （位元組） 不同於前一個呼叫或參考

A [__stdcall](../../cpp/stdcall.md)函式前面必須有原型。 否則，編譯器會解譯為原型的函式的第一個呼叫，而且當編譯器遇到不符合的呼叫，就會發生此錯誤。

若要修正此錯誤會加入函式原型。