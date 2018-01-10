---
title: __p__fmode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: __p__fmode
apilocation:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords: __p__fmode
dev_langs: C++
helpviewer_keywords: __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 341eab038db17b39e5b2a408db7c61c69d432fe9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="pfmode"></a>__p__fmode
指向 `_fmode` 全域變數會指定檔案 I/O 作業的預設「檔案轉譯模式」。  
  
## <a name="syntax"></a>語法  
  
```cpp  
int* __p__fmode(  
   );  
```  
  
## <a name="return-value"></a>傳回值  
 `_fmode` 全域變數的指標。  
  
## <a name="remarks"></a>備註  
 `__p__fmode` 函式僅供內部使用，不應該從使用者程式碼呼叫。  
  
 檔案轉譯模式會指定 [_open](../c-runtime-library/reference/open-wopen.md) 和 [_pipe](../c-runtime-library/reference/pipe.md) I/O 作業的 `binary` 或 `text` 轉譯。 如需詳細資訊，請參閱 [_fmode](../c-runtime-library/fmode.md)。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|__p\__fmode|stdlib.h|