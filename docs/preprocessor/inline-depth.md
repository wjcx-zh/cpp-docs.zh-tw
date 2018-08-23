---
title: inline_depth |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a6c8d05d326e11ecfef4df8d22cbf2b8d92bd77
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2018
ms.locfileid: "42539187"
---
# <a name="inlinedepth"></a>inline_depth
指定內嵌啟發式搜尋深度，使得它是否在深度 （在呼叫歷程圖中） 大於任何函式將予以內嵌*n*。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma inline_depth( [n] )  
```  
  
## <a name="remarks"></a>備註  
 
這個 pragma 會控制內嵌函式標示[內嵌](../cpp/inline-functions-cpp.md)並[__inline](../cpp/inline-functions-cpp.md)或在自動內嵌`/Ob2`選項。  
  
*n*可以是介於 0 和 255 之間，其中 255 表示在呼叫歷程圖中，不限的深度，而零禁止內嵌展開的值。  當*n*未指定，會使用預設值 (254)。  
  
**Inline_depth** pragma 控制可以展開一系列的函式呼叫的次數。 例如，如果內嵌深度為四，而且 A 呼叫 B，然後 B 呼叫 C，則這三個呼叫將會以內嵌方式展開。 不過，如果最接近的內嵌展開為二，則只會展開 A 和 B，C 則保持為函式呼叫。  
  
若要使用這個 pragma，您必須設定`/Ob`為 1 或 2 的編譯器選項。 使用這個 pragma 設定的深度會在 pragma 之後的第一次函式呼叫生效。  
  
內嵌深度可以在展開期間減少，但是不能增加。 如果內嵌深度為六，而在展開期間前置處理器遇到**inline_depth** pragma 搭配值為八深度會保持為六。  
  
**Inline_depth** pragma 對於標記為函式不會影響`__forceinline`。  
  
> [!NOTE]
> 遞迴函式可透過內嵌於最大 16 個呼叫深度的方式替代。  
  
## <a name="see-also"></a>另請參閱  
 
[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
[inline_recursion](../preprocessor/inline-recursion.md)