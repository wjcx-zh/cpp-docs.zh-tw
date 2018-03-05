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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d4fdaeb0e67832f4f9e0c657e48fe74a88b86292
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
-   與 Binmode.obj 連結。這會將 `_fmode` 的初始設定變更成 `_O_BINARY`，造成 `stdin`、`stdout` 和 `stderr` 以外的所有檔案都會在二進位模式中開啟。  
  
-   呼叫 `_get_fmode` 或 `_set_fmode` 以分別取得或設定 `_fmode` 全域變數。  
  
-   在您的程式中設定它，直接變更 `_fmode` 值。  
  
## <a name="see-also"></a>請參閱  
 [全域變數](../c-runtime-library/global-variables.md)   
 [_get_fmode](../c-runtime-library/reference/get-fmode.md)   
 [_set_fmode](../c-runtime-library/reference/set-fmode.md)