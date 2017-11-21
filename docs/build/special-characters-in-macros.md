---
title: "在巨集中的特殊字元 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 648122a9c8f3cf97d08128e6e12090ebc12631d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="special-characters-in-macros"></a>巨集中的特殊字元
定義會指定註解後，數字符號 （#）。 若要指定常值的數字符號在巨集中，使用插入號 (^)，做為 ^ #。  
  
 貨幣符號 （$） 指定的巨集引動過程。 若要指定常值 $，使用 $$。  
  
 若要擴充到新行的定義，行尾處以反斜線 (\\)。 叫用巨集時，反斜線加上新行字元會取代空格。 若要指定的行結尾的常值反斜線，它前面的插入號 (^)，或遵循與註解規範 （#）。  
  
 若要指定常值的新行字元，行尾的插入號 (^)、 使用中：  
  
```  
CMDS = cls^  
dir  
```  
  
## <a name="see-also"></a>另請參閱  
 [定義 NMAKE 巨集](../build/defining-an-nmake-macro.md)