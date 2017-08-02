---
title: "字元順序 | Microsoft Docs"
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
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
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
ms.openlocfilehash: 67ddf6a6712e0c98ea7b7866b3267d56308a5b5c
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="character-sequences"></a>字元順序
**ANSI 3.8.2**：原始程式檔字元序列的對應  
  
 除了不支援逸出序列以外，前置處理器陳述式使用的字元集與原始程式檔陳述式使用的相同。  
  
 因此，若要指定 Include 檔案的路徑，則只需要使用一個反斜線：  
  
```  
#include "path1\path2\myfile"  
```  
  
 在原始程式碼內必須使用兩個反斜線：  
  
```  
fil = fopen( "path1\\path2\\myfile", "rt" );  
```  
  
## <a name="see-also"></a>另請參閱  
 [前置處理指示詞](../c-language/preprocessing-directives.md)
