---
title: "前置處理器的指示詞 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 39f1e29a2bc8b72d5b2467c248a4d12b63baa26b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="directives-to-the-preprocessor"></a>前置處理器的指示詞
「指示詞」會指示 C 前置處理器在編譯之前，於程式文字上執行特定動作。 [前置處理器指示詞](../preprocessor/preprocessor-directives.md)已在《前置處理器參考》中完整說明。 這個範例會使用前置處理器指示詞 `#define`：  
  
```  
#define MAX 100  
```  
  
 這個陳述式會指示編譯器在編譯前，將出現 `MAX` 的每一個位置取代為 `100`。 C 編譯器前置處理器指示詞包括：  
  
|#define|#endif|#ifdef|#line|  
|--------------|-------------|-------------|------------|  
|`#elif`|`#error`|**#ifndef**|**#pragma**|  
|`#else`|`#if`|`#include`|`#undef`|  
  
## <a name="see-also"></a>另請參閱  
 [原始程式檔和來源程式](../c-language/source-files-and-source-programs.md)