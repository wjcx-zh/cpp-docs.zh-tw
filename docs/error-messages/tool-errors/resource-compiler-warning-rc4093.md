---
title: "資源編譯器警告 RC4093 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC4093
dev_langs: C++
helpviewer_keywords: RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4d21cbba379e72675b8957be58dc712b83673947
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-warning-rc4093"></a>資源編譯器警告 RC4093
非現用程式碼中的字元常數中包含新行  
  
 常數運算式的`#if`， `#elif`， **#ifdef**，或**#ifndef**評估為零，讓程式碼，前置處理器指示詞後面非使用中。 該非作用中的程式碼中新行字元會出現在一組單引號或雙引號。  
  
 直到下一個雙引號視為字元常數中的所有文字。