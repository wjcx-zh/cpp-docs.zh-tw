---
title: 資源編譯器警告 RC4093
ms.date: 11/04/2016
f1_keywords:
- RC4093
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
ms.openlocfilehash: 29d24f1e380f5c531e170e5dc23cf5c77eefb874
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182288"
---
# <a name="resource-compiler-warning-rc4093"></a>資源編譯器警告 RC4093

非使用中程式碼的字元常數中未轉義的分行符號

`#if`、`#elif`、 **#ifdef**或 **#ifndef**預處理器指示詞的常數運算式評估為零，使程式碼遵循非作用中。 在該非使用中的程式碼內，分行符號會出現在一組單引號或雙引號內。

所有文字，直到下一個雙引號被視為字元常數內。
