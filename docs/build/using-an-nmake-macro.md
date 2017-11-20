---
title: "使用 NMAKE 巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9893e7ec1ba29b4b5ed2ccb569a135f44b2ed47f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="using-an-nmake-macro"></a>使用 NMAKE 巨集
若要使用巨集，請其名稱前面加上貨幣符號 （$），如下所示的括號括住。  
  
## <a name="syntax"></a>語法  
  
```  
$(macroname)  
```  
  
## <a name="remarks"></a>備註  
 沒有空格。 括號是選擇性如果*巨集名稱*是單一字元。 定義字串取代 $(*巨集名稱*); 未定義的巨集取代為 null 的字串。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
 [巨集替換](../build/macro-substitution.md)  
  
## <a name="see-also"></a>另請參閱  
 [巨集和 NMAKE](../build/macros-and-nmake.md)