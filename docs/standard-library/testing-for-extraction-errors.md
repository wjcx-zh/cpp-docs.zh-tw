---
title: "測試是否有擷取錯誤 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- extraction errors
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
caps.latest.revision: 9
author: corob-msft
ms.author: corob
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 05e2c94cc23a7ad75edcd92721de538ac008d65b
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="testing-for-extraction-errors"></a>測試是否有擷取錯誤
[錯誤處理函式](../standard-library/output-file-stream-member-functions.md) 中所討論的輸出錯誤處理函式適用於輸入資料流。 務必測試擷取期間是否會發生錯誤。 請考量下列陳述式：  
  
```  
cin>> n;  
```  
  
 如果 `n` 是帶正負號的整數，則大於 32,767 (允許的最大值或 MAX_INT) 的值會設定資料流的 `fail` 位元，而 `cin` 物件會變成無法使用。 所有後續的擷取都會導致立即傳回，而且不會儲存任何值。  
  
## <a name="see-also"></a>另請參閱  
 [輸入資料流](../standard-library/input-streams.md)


