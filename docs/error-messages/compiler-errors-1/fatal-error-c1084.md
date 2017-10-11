---
title: "嚴重錯誤 C1084 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1084
dev_langs:
- C++
helpviewer_keywords:
- C1084
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: caf1e64e91871087c9e47860a41c2824a811295a
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

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
