---
title: "前置處理器的指示詞 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: e5d4790cccc280a6a2d23a66c6959fd07bdefa9b
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

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
