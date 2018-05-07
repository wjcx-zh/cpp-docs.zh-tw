---
title: 資源編譯器錯誤 RC2101 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2101
dev_langs:
- C++
helpviewer_keywords:
- RC2101
ms.assetid: 580f9d74-162f-41e9-9438-ddbe3457c359
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b07f6211e1cc36bd471b04126e724e42eb610641
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-error-rc2101"></a>資源編譯器錯誤 RC2101
無效的指示詞在前置處理過的 RC 檔  
  
 資源編譯器檔案包含 **#pragma**指示詞。  
  
 使用 **#ifndef**與資源編譯器定義它會處理包含檔案的 RC_INVOKED 常數的前置處理器指示詞。 位置 **#pragma**指示詞的定義 RC_INVOKED 常數時未處理的程式碼區塊內。 只能由 C/c + + 編譯器，而不是由資源編譯器處理區塊中的程式碼。 下列程式碼範例示範這項技術：  
  
```  
#ifndef RC_INVOKED  
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler  
#endif  
```  
  
 **#Pragma**前置處理器指示詞沒有任何意義。RC 檔。 **#Include**中經常使用前置處理器指示詞。RC 檔包含標頭檔 （以專案為基礎的自訂標頭檔或使用其中一個產品由 Microsoft 提供的標準標頭檔）。 其中包括檔案包含 **#pragma**指示詞。 由於標頭檔可包含一或多個其他標頭檔，包含違反檔案 **#pragma**指示詞可能無法馬上看得出來。  
  
 **#Ifndef** RC_INVOKED 技術可以控制包括專案為基礎的標頭檔中的標頭檔。