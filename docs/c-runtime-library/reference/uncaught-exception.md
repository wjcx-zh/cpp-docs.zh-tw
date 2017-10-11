---
title: __uncaught_exception | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __uncaught_exception
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- __uncaught_exception
dev_langs:
- C++
helpviewer_keywords:
- __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
caps.latest.revision: 2
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 2b43a6b08087dcaeeda7959eaadbee9c250f4de9
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="uncaughtexception"></a>__uncaught_exception
表示是否已擲回一或多個例外狀況，但尚未由 [try-catch](../../cpp/try-throw-and-catch-statements-cpp.md) 陳述式之對應的 `catch` 區塊所處理。  
  
## <a name="syntax"></a>語法  
  
```cpp  
bool __uncaught_exception(  
   );  
```  
  
## <a name="return-value"></a>傳回值  
 從 `try` 區塊擲回例外狀況，一直到相符的 `catch` 區塊已初始化為止都是 `true`，否則為 `false`。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|__uncaught_exception|eh.h|  
  
## <a name="see-also"></a>另請參閱  
 [try、throw 和 catch 陳述式 (C++)](../../cpp/try-throw-and-catch-statements-cpp.md)
