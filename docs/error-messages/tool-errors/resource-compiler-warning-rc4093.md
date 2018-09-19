---
title: 資源編譯器警告 RC4093 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC4093
dev_langs:
- C++
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b1ca04b17ebdb9d48bc94032482caf48ad4aa00
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111559"
---
# <a name="resource-compiler-warning-rc4093"></a>資源編譯器警告 RC4093

在非使用中的程式碼中的字元常數中的未逸出新行

常數運算式`#if`， `#elif`， **#ifdef**，或 **#ifndef**被評估為零，使程式碼的前置處理器指示詞會遵循非使用中。 在非使用中的程式碼中，新行字元會出現在一組單引號或雙引號的引號內。

直到下一個雙引號視為要在字元常數中的所有文字。