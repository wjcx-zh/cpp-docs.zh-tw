---
title: "緩衝的效果 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- buffers, effects of buffering
- buffering, effects of
ms.assetid: 5d544812-e95e-4f28-b15a-edef3f3414fd
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: e834b5be6b7d31d1f1516799462d57330bf4ceb2
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="effects-of-buffering"></a>緩衝的效果
下例會示範緩衝的效果。 您可能希望程式會列印 `please wait`，請等 5 秒鐘，然後再繼續。 不過，它不一定這樣運行，因為輸出經過緩衝處理。  
  
```  
// effects_buffering.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <time.h>  
using namespace std;  
  
int main( )  
{  
   time_t tm = time( NULL ) + 5;  
   cout << "Please wait...";  
   while ( time( NULL ) < tm )  
      ;  
   cout << "\nAll done" << endl;  
}  
```  
  
 若要讓程式按邏輯工作， `cout` 物件必須在訊息要出現時清空自己本身。 若要排清 `ostream` 物件，請將 `flush` 操作工具傳給它：  
  
```  
cout <<"Please wait..." <<flush;  
```  
  
 這個步驟會排清緩衝區，確保訊息在等待前即印出。 您也可以使用`endl`操作工具，排清緩衝區以及輸出歸位字元傳回的換行，或者您可以使用`cin`物件。 這個物件 (與 `cerr` 或 `clog` 物件) 通常會繫結至 `cout` 物件。 因此，只要使用 `cin` (或 `cerr` 或 `clog` 物件) 就會排清 `cout` 物件。  
  
## <a name="see-also"></a>另請參閱  
 [輸出資料流](../standard-library/output-streams.md)


