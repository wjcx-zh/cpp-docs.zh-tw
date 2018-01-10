---
title: "Makefile 中的特殊字元 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, special characters
- makefiles, special characters
- special characters, in NMAKE macros
- macros, special characters
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6c574040d6004516682379a5e64b87c1b92388ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="special-characters-in-a-makefile"></a>Makefile 中的特殊字元
若要使用 NMAKE 特殊字元做為常值字元，將插入號 (^) 前面。 NMAKE 會忽略其他字元在前面的插入號。 特殊字元都是：  
  
 `:  ;  #  (  )  $  ^  \  {  }  !  @  —`  
  
 有引號的字串中的插入號 (^) 會被視為常值插入號字元。 一行結尾處的插入號插入常值的新行字元在字串、 巨集。  
  
 在巨集中，反斜線 (\\) 接著新行字元會以空格取代。  
  
 在命令中的百分比符號 （%） 會是檔案規範。 若要表示 %常值中的命令，請指定雙百分比符號 （%） 個。 在其他情況下，NMAKE 解譯單一 %字面意義，但是永遠會解譯 double %%做為單一 %。 因此，代表常值 %%，指定可能是三個百分比符號，%%%，或四個百分比符號 %%%。  
  
 若要使用貨幣符號 （$） 做為常值字元，在命令中，指定兩個貨幣符號 （$$）。 這個方法也可用在其他情況下其中 ^ $ 運作。  
  
## <a name="see-also"></a>請參閱  
 [Makefile 內容](../build/contents-of-a-makefile.md)