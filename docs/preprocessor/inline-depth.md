---
title: "inline_depth |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- inline_depth_CPP
- vc-pragma.inline_depth
dev_langs:
- C++
helpviewer_keywords:
- pragmas, inline_depth
- inline_depth pragma
ms.assetid: 2bba60fe-43ea-4d09-90f7-aafaba3bad07
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a3738e1e2217de7e8617f91a36218718cf756ca3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="inlinedepth"></a>inline_depth
指定內嵌啟發式搜尋深度，這樣一來，如果函式的深度 (在呼叫圖形中) 大於 `n`，就不會將該函式內嵌。  
  
## <a name="syntax"></a>語法  
  
```  
  
#pragma inline_depth( [n] )  
```  
  
## <a name="remarks"></a>備註  
 這個 pragma 會控制內嵌函式標示為[內嵌](../cpp/inline-functions-cpp.md)和[__inline](../cpp/inline-functions-cpp.md)或內嵌自動在 /Ob2 選項底下。  
  
 `n` 可以是介於 0 和 255 之間的值，其中 255 表示在呼叫圖形中不限深度，而零則表示禁止內嵌展開。  若未指定 `n`，則會使用預設值 (254)。  
  
 **Inline_depth** pragma 控制一系列的函式呼叫項目可展開的次數。 例如，如果內嵌深度為四，而且 A 呼叫 B，然後 B 呼叫 C，則這三個呼叫將會以內嵌方式展開。 不過，如果最接近的內嵌展開為二，則只會展開 A 和 B，C 則保持為函式呼叫。  
  
 若要使用這個 pragma，您必須將 /Ob 編譯器選項設定為 1 或 2。 使用這個 pragma 設定的深度會在 pragma 之後的第一次函式呼叫生效。  
  
 內嵌深度可以在展開期間減少，但是不能增加。 如果內嵌深度為六，而在展開期間前置處理器遇到**inline_depth** 8 深度的值會保持為六。  
  
 **Inline_depth** pragma 已標記為函式不會影響`__forceinline`。  
  
> [!NOTE]
>  遞迴函式可透過內嵌於最大 16 個呼叫深度的方式替代。  
  
## <a name="see-also"></a>請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [inline_recursion](../preprocessor/inline-recursion.md)