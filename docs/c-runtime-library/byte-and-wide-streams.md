---
title: "位元組和寬資料流 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Byte and Wide Streams
dev_langs:
- C++
helpviewer_keywords:
- byte streams
- wide streams
ms.assetid: 61ef0587-4cbc-4eb8-aae5-4c298dbbc6f9
caps.latest.revision: 8
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: c916caf1ee0b39567813921401ee02cbda83d222
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="byte-and-wide-streams"></a>位元組和寬資料流
位元組資料流會將檔案視為位元組順序。 在程式內，資料流是相同的位元組順序。  
  
 相對地，寬資料流將檔案視為一般化的多位元組字元，它可以有廣為更廣的編碼規則 (文字與二進位檔案仍以先前描述的方式讀取及寫入)。在程式內，資料流看起來就像是對應的寬字元順序。 在兩個表示之間進行的轉換會在「標準 C 程式庫」中進行。 原則上，轉換規則可以由會觸發類別 `LC_CTYPE` 的 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 呼叫來修改。 每個寬資料流都會在成為寬資料流時決定其轉換規則，而且即使類別 `LC_CTYPE` 後續發生變更，也會保留這些規則。  
  
 在寬資料流中定位面臨與文字資料流相同的限制。 此外，檔案位置指標可能必須處理狀態相依編碼。 它通常同時包含資料流內的位元組位移。以及類型為 `mbstate_t` 的物件。 因此，取得寬資料流內檔案位置的唯一可靠方式是呼叫 [fgetpos](../c-runtime-library/reference/fgetpos.md)，而還原以此方式取得之位置的唯一可靠方式是呼叫 [fsetpos](../c-runtime-library/reference/fsetpos.md)。  
  
## <a name="see-also"></a>另請參閱  
 [檔案和資料流](../c-runtime-library/files-and-streams.md)   
 [setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)
