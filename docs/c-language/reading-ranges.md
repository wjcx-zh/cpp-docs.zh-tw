---
title: "讀取範圍 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 96748c24fbf1e5adfebb72ba809533afeafebe38
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="reading-ranges"></a>讀取範圍
**ANSI 4.9.6.2**：解譯虛線 (-) 字元，該字元不是 `fscanf` 函式中 % [ 轉換之 scanlist 中的第一個字元，也不是最後一個字元  
  
 下面這行  
  
```  
fscanf( fileptr, "%[A-Z]", strptr);  
```  
  
 會將範圍 A-Z 中任何數目的字元讀取到 `strptr` 所指向的字串中。  
  
## <a name="see-also"></a>另請參閱  
 [程式庫函式](../c-language/library-functions.md)