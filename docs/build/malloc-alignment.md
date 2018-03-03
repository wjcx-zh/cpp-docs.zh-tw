---
title: "malloc 對齊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: a8d1d1b4-5122-456f-9a64-a50e105e55a5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d9acaf1c8912e1b563bb5d05ae600d1430049e6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="malloc-alignment"></a>malloc 對齊
[malloc](../c-runtime-library/reference/malloc.md)保證會傳回已適當地對齊儲存具有基本的對齊方式，以及任何物件配置的記憶體無法容納的記憶體。 A*基本對齊*是小於或等於不對齊規格的實作所支援的最大對齊的對齊方式。 (在 Visual c + + 中，這是所需的對齊`double`，或 8 個位元組。 在以 64 位元平台為目標的程式碼中，則為 16 個位元組)。比方說，四個位元組配置則會支援任何四個位元組或較小物件的界限上對齊。  
  
 Visual c + + 允許具有型別*擴充對齊*，這也稱為是*過度對齊*型別。 比方說，SSE 類型[__m128](../cpp/m128.md)和`__m256`，以及使用所宣告的型別`__declspec(align( n ))`其中`n`大於 8，已延伸對齊方式。 由不保證適用於需要擴充的對齊的物件的界限上的記憶體對齊`malloc`。 若要針對過度對齊類型配置記憶體，請使用[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)和相關函式。  
  
## <a name="see-also"></a>請參閱  
 [堆疊使用方式](../build/stack-usage.md)   
 [對齊](../cpp/align-cpp.md)   
 [__declspec](../cpp/declspec.md)