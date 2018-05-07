---
title: 資源編譯器警告 RC4093 |Microsoft 文件
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
ms.openlocfilehash: e9cca3c2a139e1109746f3a690cfb3f31509a9fe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-warning-rc4093"></a>資源編譯器警告 RC4093
非現用程式碼中的字元常數中包含新行  
  
 常數運算式的`#if`， `#elif`， **#ifdef**，或 **#ifndef**評估為零，讓程式碼，前置處理器指示詞後面非使用中。 該非作用中的程式碼中新行字元會出現在一組單引號或雙引號。  
  
 直到下一個雙引號視為字元常數中的所有文字。