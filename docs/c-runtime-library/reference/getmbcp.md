---
title: _getmbcp | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getmbcp
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getmbcp
- getmbcp
dev_langs:
- C++
helpviewer_keywords:
- code pages, determining current
- _getmbcp function
- getmbcp function
ms.assetid: 2db202d4-5c3d-4871-a0b8-ceb0b79ee7bb
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 4bc1000e9443d60e966ef6a929ed134acd44f1b7
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="getmbcp"></a>_getmbcp
擷取目前的字碼頁。  
  
## <a name="syntax"></a>語法  
  
```  
int _getmbcp( void );  
```  
  
## <a name="return-value"></a>傳回值  
 傳回目前的多位元組字碼頁。 傳回值 0 表示使用中的是單一位元組字碼頁。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_getmbcp`|\<mbctype.h>|  
  
 如需相容性詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)
