---
title: 巨集和 c + + |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 746b04113e4cb49716e0c1fa6dee69a250bded42
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="macros-and-c"></a>巨集和 C++
C++ 提供的新功能，其中取代了一些由 ANSI C 前置處理器提供的功能。 這些新功能可強化此語言的類型安全及可預測性：  
  
-   C + + 物件宣告為**const**可用在常數運算式中。 這可讓程式宣告具有類型和值資訊的常數，以及可以由偵錯工具以符號形式檢視的列舉。 使用前置處理器 `#define` 指示詞來定義常數會不夠精確。 任何存放裝置配置給**const**除非取得其位址的運算式在程式中找到的物件。  
  
-   C++ 內嵌函式功能取代了函式類型的巨集。 在巨集中使用內嵌函式的優點包括：  
  
    -   類型安全。 內嵌函式的類型檢查限制與一般函式相同。 巨集不是安全的類型。  
  
    -   修正具有副作用的引數處理。 在進入函式主體之前，內嵌函式會將所提供的運算式當做引數進行評估。 因此，沒有機會讓具有副作用的運算式不安全。  
  
 如需有關內嵌函式的詳細資訊，請參閱[inline、 __inline、 \__forceinline](../cpp/inline-functions-cpp.md)。  
  
 為了提供回溯相容性，Microsoft C++ 會保留存在於 ANSI C 和舊版 C++ 規格中的所有前置處理器功能。  
  
## <a name="see-also"></a>另請參閱  
 [預先定義巨集](../preprocessor/predefined-macros.md)   
 [巨集 (C/C++)](../preprocessor/macros-c-cpp.md)