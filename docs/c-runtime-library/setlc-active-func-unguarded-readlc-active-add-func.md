---
title: "___setlc_active_func、___unguarded_readlc_active_add_func | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
apilocation:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- ___unguarded_readlc_active_add_func
- ___setlc_active_func
dev_langs:
- C++
helpviewer_keywords:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
ms.assetid: 605ec4e3-81e5-4ece-935a-f434768cc702
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: a1746d597613bf76bdbf8c38ff3487b4d0c18fc2
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="setlcactivefunc-unguardedreadlcactiveaddfunc"></a>___setlc_active_func、___unguarded_readlc_active_add_func
已過時。 CRT 只會為保留二進位相容性匯出這些內部函式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
int ___setlc_active_func(void);  
int * ___unguarded_readlc_active_add_func(void);  
```  
  
## <a name="return-value"></a>傳回值  
 傳回的值並不重要。  
  
## <a name="remarks"></a>備註  
 雖然內部 CRT 函式 `___setlc_active_func` 和 `___unguarded_readlc_active_add_func` 已過時且不再提供使用，CRT 程式庫還是會為了保留二進位相容性匯出這些函式。 `___setlc_active_func` 的最初目的是要將目前作用中呼叫數傳回至 `setlocale` 函式。 `___unguarded_readlc_active_add_func` 的最初目的是要在不鎖定地區設定的情況下，傳回參考地區設定的函式數。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`___setlc_active_func`, `___unguarded_readlc_active_add_func`|無|  
  
## <a name="see-also"></a>另請參閱  
 [setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)
