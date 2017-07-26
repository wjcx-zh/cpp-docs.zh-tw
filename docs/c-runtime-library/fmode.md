---
title: _fmode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- fmode
- _fmode
dev_langs:
- C++
helpviewer_keywords:
- file translation [C++], default mode
- fmode function
- _fmode function
ms.assetid: ac6df9eb-e5cc-4c54-aff3-373c21983118
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 3c0946419e1c0a408a7dfad190387f0165d9fba0
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="fmode"></a>_fmode
`_fmode` 變數會設定文字或二進位轉譯的預設檔案轉譯模式。 這個全域變數已為 [_get_fmode](../c-runtime-library/reference/get-fmode.md) 和 [_set_fmode](../c-runtime-library/reference/set-fmode.md) 的更安全版本所取代，它們應該用來取代全域變數。 它會在 Stdlib.h 中宣告，如下所示。  
  
## <a name="syntax"></a>語法  
  
```  
extern int _fmode;  
```  
  
## <a name="remarks"></a>備註  
 `_fmode` 的預設設定是文字模式轉譯的 `_O_TEXT`。 `_O_BINARY` 是二進位模式的設定。  
  
 您有三種方式可以變更 `_fmode` 值：  
  
-   與 Binmode.obj 連結。 這會將 `_fmode` 的初始設定變更成 `_O_BINARY`，造成 `stdin`、`stdout` 和 `stderr` 以外的所有檔案都會在二進位模式中開啟。  
  
-   呼叫 `_get_fmode` 或 `_set_fmode` 以分別取得或設定 `_fmode` 全域變數。  
  
-   在您的程式中設定它，直接變更 `_fmode` 值。  
  
## <a name="see-also"></a>另請參閱  
 [全域變數](../c-runtime-library/global-variables.md)   
 [_get_fmode](../c-runtime-library/reference/get-fmode.md)   
 [_set_fmode](../c-runtime-library/reference/set-fmode.md)
