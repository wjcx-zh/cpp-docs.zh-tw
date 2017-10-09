---
title: "_acmdln、_tcmdln、_wcmdln | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wcmdln
- _acmdln
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _acmdln
- acmdln
- _wcmdln
- wcmdln
- _tcmdln
- tcmdln
dev_langs:
- C++
helpviewer_keywords:
- _wcmdln global variable
- wcmdln global variable
- _acmdln global variable
- _tcmdln global variable
- tcmdln global variable
- acmdln global variable
ms.assetid: 4fc0a6a0-3f93-420a-a19f-5276061ba539
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: a713978e44762d5e4c771112ef5adf256a9475c6
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="acmdln-tcmdln-wcmdln"></a>_acmdln、_tcmdln、_wcmdln
內部 CRT 全域變數。 命令列。  
  
## <a name="syntax"></a>語法  
  
```  
char * _acmdln;  
wchar_t * _wcmdln;  
  
#ifdef WPRFLAG  
   #define _tcmdln _wcmdln  
#else  
   #define _tcmdln _acmdln  
```  
  
## <a name="remarks"></a>備註  
 這些 CRT 內部變數會儲存完整的命令列。 這些變數會在 CRT 的已匯出符號中公開，而不是供您用於程式碼中。 `_acmdln` 將資料儲存為字元字串。 `_wcmdln` 將資料儲存為寬字元字串。 `_tcmdln` 可定義為 `_acmdln` 或 `_wcmdln`，這要取決於哪個較合適。  
  
## <a name="see-also"></a>另請參閱  
 [全域變數](../c-runtime-library/global-variables.md)
