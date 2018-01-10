---
title: "#<a name=\"undef-directive-cc--microsoft-docs\"></a>undef 指示詞 （C/c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '#undef'
dev_langs: C++
helpviewer_keywords:
- '#undef directive'
- undef directive (#undef)
- preprocessor, directives
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aee7babf895b72a5ff4f5fb1485e4bb118e95889
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="undef-directive-cc"></a>#undef 指示詞 (C/C++)
移除 (取消定義) 先前使用 `#define` 建立的名稱。  
  
## <a name="syntax"></a>語法  
  
```  
  
#undef   
identifier  
  
```  
  
## <a name="remarks"></a>備註  
 `#undef`指示詞會移除目前的定義*識別碼*。 因此，後續發生次數*識別碼*由前置處理器會被忽略。 若要移除巨集的定義使用`#undef`，提供的巨集*識別碼*; 不會提供參數清單。  
  
 您也可以將 `#undef` 指示詞套用至沒有先前定義的識別項。 這樣可確保識別項處於未定義狀態。 巨集取代不會在 `#undef` 陳述式內執行。  
  
 `#undef` 指示詞通常會與 `#define` 指示詞配對，以便在原始程式中建立識別項在其中具有特殊意義的區域。 例如，原始程式的特定函式可以使用資訊清單常數，以定義不會影響程式其他部分的環境特定值。 `#undef` 指示詞也可搭配 `#if` 指示詞，以控制原始程式的條件式編譯。 請參閱[#if、 #elif、 #else 和 #endif 指示詞](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)如需詳細資訊。  
  
 在下列範例中，`#undef` 指示詞會移除符號常數和巨集的定義。 請注意，其中只會提供巨集的識別項。  
  
```  
#define WIDTH 80  
#define ADD( X, Y ) ((X) + (Y))  
.  
.  
.  
#undef WIDTH  
#undef ADD  
```  
  
 **Microsoft 特定的**  
  
 您可以從命令列使用 /U 選項，後面接著要取消定義的巨集名稱，藉此取消巨集的定義。 發出此命令的效果相當於一連串`#undef`*巨集名稱*陳述式開頭的檔案。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [前置處理器指示詞](../preprocessor/preprocessor-directives.md)