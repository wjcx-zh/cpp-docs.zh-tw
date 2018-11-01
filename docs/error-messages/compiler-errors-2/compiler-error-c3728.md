---
title: 編譯器錯誤 C3728
ms.date: 11/04/2016
f1_keywords:
- C3728
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
ms.openlocfilehash: 68aa23843b0470f15f409b6f3b58624f979ccfae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454583"
---
# <a name="compiler-error-c3728"></a>編譯器錯誤 C3728

'event': 事件沒有引發方法

中繼資料建立與語言，例如 C# 中，不允許它定義在類別之外，從引發事件，所含[#using](../../preprocessor/hash-using-directive-cpp.md)指示詞，而是使用 CLR 程式設計嘗試的 Visual c + + 程式引發事件。

若要引發事件，例如 C# 語言開發的程式中，包含事件的類別必須也定義公用方法來引發事件。