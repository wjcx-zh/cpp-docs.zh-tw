---
title: fwide | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fwide
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
- fwide
dev_langs:
- C++
helpviewer_keywords:
- fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: f10bd98a6dedba2181aa1d5ebba60f64dda093be
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="fwide"></a>fwide
未實作。  
  
## <a name="syntax"></a>語法  
  
```  
int fwide(  
   FILE *stream,  
   int mode;  
);  
```  
  
#### <a name="parameters"></a>參數  
 `stream`  
 `FILE` 結構的指標 (忽略)。  
  
 `mode`  
 資料流的新寬度︰寬字元為正值、位元組為負值、零則保留不變。 (這個值會被忽略。)  
  
## <a name="return-value"></a>傳回值  
 此函式目前只會傳回 `mode`。  
  
## <a name="remarks"></a>備註  
 此函式的目前版本不符合標準。  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭|  
|--------------|---------------------|  
|`fwide`|\<wchar.h>|  
  
 如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。
