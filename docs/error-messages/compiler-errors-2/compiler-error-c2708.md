---
title: 編譯器錯誤 C2708 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2708
dev_langs:
- C++
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0accd68881cccad5e34530a6c157a4e8179b283
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111091"
---
# <a name="compiler-error-c2708"></a>編譯器錯誤 C2708

'identifier': 實質參數長度 （位元組） 不同於前一個呼叫或參考

A [__stdcall](../../cpp/stdcall.md)函式前面必須有原型。 否則，編譯器會解譯為原型的函式的第一個呼叫，而且當編譯器遇到不符合的呼叫，就會發生此錯誤。

若要修正此錯誤會加入函式原型。