---
title: 編譯器錯誤 C2708
ms.date: 11/04/2016
f1_keywords:
- C2708
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
ms.openlocfilehash: a1d3379a0da42c5aabd38cffbf6f6a3f340ef3b9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202367"
---
# <a name="compiler-error-c2708"></a>編譯器錯誤 C2708

' identifier '：實際參數長度（以位元組為單位）與先前的呼叫或參考不同

[__Stdcall](../../cpp/stdcall.md)函數的前面必須加上原型。 否則，編譯器會將函式的第一個呼叫解讀為原型，而當編譯器遇到不符合的呼叫時，就會發生此錯誤。

若要修正這個錯誤，請新增函數原型。
