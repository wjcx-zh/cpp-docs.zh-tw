---
title: 讀取範圍 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8ebad4bfda77238ad8c861410e2af5453df73af
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="reading-ranges"></a>讀取範圍
**ANSI 4.9.6.2**：解譯虛線 (-) 字元，該字元不是 `fscanf` 函式中 % [ 轉換之 scanlist 中的第一個字元，也不是最後一個字元  
  
 下面這行  
  
```  
fscanf( fileptr, "%[A-Z]", strptr);  
```  
  
 會將範圍 A-Z 中任何數目的字元讀取到 `strptr` 所指向的字串中。  
  
## <a name="see-also"></a>請參閱  
 [程式庫函式](../c-language/library-functions.md)