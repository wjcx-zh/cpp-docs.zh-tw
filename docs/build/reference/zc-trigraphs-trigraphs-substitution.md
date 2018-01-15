---
title: "-Zc： 三併詞 （三併詞替代） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /Zc
dev_langs: C++
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 739e772c87c937a552e07a32fa5bb80b1a1e2508
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs (三併詞替代)
當**/zc: trigraphs**指定，則編譯器會使用對應的標點符號字元取代三併詞的字元序列。 若要關閉三併詞替代，指定**/Zc:trigraphs-**。 根據預設， **/zc: trigraphs**已關閉。  
  
## <a name="syntax"></a>語法  
  
```  
/Zc:trigraphs[-]  
```  
  
## <a name="remarks"></a>備註  
 三併詞包含兩個連續的問號 ("？") 後接唯一的第三個字元。 例如，編譯器會取代"??="三併詞使用 '#' 字元。 若在 C 原始程式檔中使用的字元集不含某些標點符號字元的慣用圖形表示，您可改用三併詞。  
  
 如需 C/c + + 三併詞，並以範例顯示如何使用三併詞的清單，請參閱[三併詞](../../c-language/trigraphs.md)。  
  
## <a name="see-also"></a>請參閱  
 [/Zc （一致性）](../../build/reference/zc-conformance.md)   
 [三併詞](../../c-language/trigraphs.md)