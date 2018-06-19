---
title: _acmdln、_tcmdln、_wcmdln | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 141e261af618cc6058a2a731b70e824582be303b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386491"
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
  
## <a name="see-also"></a>請參閱  
 [全域變數](../c-runtime-library/global-variables.md)