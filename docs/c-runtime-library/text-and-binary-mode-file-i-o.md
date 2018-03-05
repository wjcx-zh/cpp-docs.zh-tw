---
title: "文字和二進位模式檔案 I-O | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- files [C++], open functions
- I/O [CRT], text files
- functions [CRT], file access
- binary access, binary mode file I/O
- translation, modes
- I/O [CRT], binary
- text files, I/O
- I/O [CRT], translation modes
- translation modes (file I/O)
- binary access
ms.assetid: 3196e321-8b87-4609-b302-cd6f3c516051
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 50387aa2512e38a4e9f13fdfb1b042c3df2de45c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="text-and-binary-mode-file-io"></a>文字和二進位模式檔案 I/O
檔案 I/O 作業是在兩種轉譯模式 (文字或二進位) 的其中一種完成，取決於開啟檔案時使用的模式。 資料檔案通常是在文字模式中處理。 若要控制檔案轉譯模式，您可以：  
  
-   維持目前的預設設定，並只在開啟選取的檔案時才指定替代模式。  
  
-   使用函式 [_set_fmode](../c-runtime-library/reference/set-fmode.md) 來變更新開啟之檔案的預設模式。 使用 [_get_fmode](../c-runtime-library/reference/get-fmode.md) 來尋找目前的預設模式。 初始預設設定是文字模式 (`_O_TEXT`)。  
  
-   透過在您的程式中設定全域變數 [_fmode](../c-runtime-library/fmode.md) 來變更預設轉譯模式。 函式 `_set_fmode` 可設定此變數的值，但您也可以直接設定此變數的值。  
  
 當您呼叫 file-open 函式 (例如 [_open](../c-runtime-library/reference/open-wopen.md)、[fopen](../c-runtime-library/reference/fopen-wfopen.md)、[fopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)、[freopen](../c-runtime-library/reference/freopen-wfreopen.md)、[freopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)[_fsopen](../c-runtime-library/reference/fsopen-wfsopen.md) 或 [_sopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)) 時，可以透過為函式 [_set_fmode](../c-runtime-library/reference/set-fmode.md) 指定適當的引數來覆寫 `_fmode` 的目前預設設定。 `stdin`、`stdout` 與 `stderr` 資料流預設一律會在文字模式中開啟，但您也可以在開啟這些檔案時覆寫此預設值。 在檔案開啟後，使用 [_setmode](../c-runtime-library/reference/setmode.md) 利用檔案描述項來變更轉譯模式。  
  
## <a name="see-also"></a>請參閱  
 [輸入和輸出](../c-runtime-library/input-and-output.md)   
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)