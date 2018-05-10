---
title: 轉譯模式常數 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _O_BINARY
- _O_TEXT
- _O_RAW
dev_langs:
- C++
helpviewer_keywords:
- O_BINARY constant
- O_TEXT constant
- O_RAW constant
- _O_TEXT constant
- _O_RAW constant
- translation constants
- _O_BINARY constant
- translation, constants
- translation, modes
- translation modes (file I/O)
ms.assetid: a5993bf4-7e7a-47f9-83c3-e46332b85579
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eabf83c8388819b074ad553dc2b29b1902f2f1b5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="translation-mode-constants"></a>轉譯模式常數
## <a name="syntax"></a>語法  
  
```  
  
#include <fcntl.h>  
  
```  
  
## <a name="remarks"></a>備註  
 `_O_BINARY` 和 `_O_TEXT` 資訊清單常數判斷檔案的轉譯模式 (`_open` 和 `_sopen`) 或資料流的轉譯模式 (`_setmode`)。  
  
 允許的值包括：  
  
 `_O_TEXT`  
 以文字 (已轉譯) 模式開啟檔案。 歸位/換行字元 (CR-LF) 的組合會在輸入中轉譯為單行換行字元 (LF)。 換行字元會在輸出中轉譯為 CR-LF 組合。 此外，Ctrl+Z 會在輸入中解譯成檔案結尾字元。 在為了讀取和讀取/寫入而開啟的檔案中，`fopen` 會盡可能檢查檔案結尾是否有 Ctrl+Z，並加以移除。 這樣做的原因是因為使用 `fseek` 和 `ftell` 函式在以 Ctrl+Z 結束的檔案內移動可能會讓 `fseek` 在檔案結尾附近產生不當行為。  
  
 `_O_BINARY`  
 以二進位 (未轉譯) 模式開啟檔案。 會隱藏上述轉譯。  
  
 `_O_RAW`  
 與 `_O_BINARY` 相同。 支援 C 2.0 相容性。  
  
 如需詳細資訊，請參閱[文字和二進位模式檔案 I/O](../c-runtime-library/text-and-binary-mode-file-i-o.md) 和[檔案轉譯](../c-runtime-library/file-translation-constants.md)。  
  
## <a name="see-also"></a>請參閱  
 [_open、_wopen](../c-runtime-library/reference/open-wopen.md)   
 [_pipe](../c-runtime-library/reference/pipe.md)   
 [_sopen、_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [_setmode](../c-runtime-library/reference/setmode.md)   
 [全域常數](../c-runtime-library/global-constants.md)