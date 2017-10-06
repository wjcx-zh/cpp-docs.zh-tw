---
title: __setusermatherr | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __setusermatherr
apilocation:
- msvcr80.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __setusermatherr
dev_langs:
- C++
helpviewer_keywords:
- __setusermatherr
ms.assetid: f306818d-381a-4d68-8739-71b92bacb5ea
caps.latest.revision: 2
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 43b4b5ec6cddcb4a325201a4f9e2afe02ef9454a
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="setusermatherr"></a>__setusermatherr
指定用使用者提供的常式處理算術錯誤，不用 [_matherr](../c-runtime-library/reference/matherr.md) 常式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void __setusermatherr(  
   _HANDLE_MATH_ERROR pf   
   )  
```  
  
#### <a name="parameters"></a>參數  
 `pf`  
 使用者提供的 `_matherr` 實作指標。  
  
 `pf` 參數的類型宣告為 `typedef int (__cdecl * _HANDLE_MATH_ERROR)(struct _exception *)`。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|__setusermatherr|matherr.c|
