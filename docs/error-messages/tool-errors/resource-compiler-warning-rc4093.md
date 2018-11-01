---
title: 資源編譯器警告 RC4093
ms.date: 11/04/2016
f1_keywords:
- RC4093
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
ms.openlocfilehash: 23bf436e6e8338f89bc576564181c84715028332
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541878"
---
# <a name="resource-compiler-warning-rc4093"></a>資源編譯器警告 RC4093

在非使用中的程式碼中的字元常數中的未逸出新行

常數運算式`#if`， `#elif`， **#ifdef**，或 **#ifndef**被評估為零，使程式碼的前置處理器指示詞會遵循非使用中。 在非使用中的程式碼中，新行字元會出現在一組單引號或雙引號的引號內。

直到下一個雙引號視為要在字元常數中的所有文字。