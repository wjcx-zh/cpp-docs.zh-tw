---
title: 嚴重錯誤 C1084 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1084
dev_langs:
- C++
helpviewer_keywords:
- C1084
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7266a2158c3e6ccd02ea82de22c6f90a8b6363d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229385"
---
# <a name="fatal-error-c1084"></a>嚴重錯誤 C1084
無法閱讀 filetype 檔案：'file' : 訊息  
  
 此錯誤通常因編譯器呼叫內部系統 API 失敗所導致。 顯示當發生此錯誤的訊息通常會產生由[_wcserror_s](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)或[FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351.aspx)。  
  
 執行下列步驟，可能有助於解決 C1084：  
  
-   確保指定的檔案存在。  
  
-   確保設定適當的權限，以存取指定的檔案。  
  
-   請確定命令列語法中所述的規則就會遵守[編譯器命令列語法](../../build/reference/compiler-command-line-syntax.md)。  
  
-   確定已正確環境變數**TMP**和**TEMP**具有正確的設定，以及適當的權限，才能存取這些環境變數所參考的目錄。 也請確定所參考的磁碟機**TMP**和**TEMP**環境變數包含足夠的可用空間量。  
  
-   如果訊息指出「錯誤的檔案號碼」，則指定的檔案可能已在前景關閉，而在背景編譯。  
  
 在執行上述診斷之後，執行清除組建。