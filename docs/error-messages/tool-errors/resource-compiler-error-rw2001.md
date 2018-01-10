---
title: "資源編譯器錯誤 RW2001 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RW2001
dev_langs: C++
helpviewer_keywords: RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1a14cd36ab87297cf5bc0aa547bdea5ef23260e8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rw2001"></a>資源編譯器錯誤 RW2001
無效的指示詞在前置處理過的 RC 檔  
  
 RC 檔包含**#pragma**指示詞。  
  
 使用**#ifndef**前置處理器指示詞中的**RC_INVOKED**常數資源編譯器定義它會處理包含檔案。 位置**#pragma**指示詞的非程式碼區塊中處理時**RC_INVOKED**常數定義。 只能由 C/c + + 編譯器，而不是由資源編譯器處理區塊中的程式碼。 下列程式碼範例示範這項技術：  
  
```  
#ifndef RC_INVOKED  
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler  
#endif  
```  
  
 **#Pragma**前置處理器指示詞沒有任何意義。RC 檔。 **#Include**中經常使用前置處理器指示詞。RC 檔包含標頭檔 （以專案為基礎的自訂標頭檔或使用其中一個產品由 Microsoft 提供的標準標頭檔）。 其中包括檔案包含**#pragma**指示詞。 由於標頭檔可包含一或多個其他標頭檔，包含違反檔案**#pragma**指示詞可能無法馬上看得出來。  
  
 **#Ifndef RC_INVOKED**技術可以控制包括專案為基礎的標頭檔中的標頭檔。