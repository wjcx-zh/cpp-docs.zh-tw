---
title: "_initterm、_initterm_e | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _initterm_e
- _initterm
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _initterm_e
- initterm
- _initterm
- initterm_e
dev_langs: C++
helpviewer_keywords:
- initterm function
- initterm_e function
- _initterm function
- _initterm_e function
ms.assetid: 85131efe-c747-429a-8897-bcdedb000172
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 95f508b1198cd009abe0cf82cbe9a7aaf553240f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="initterm-initterme"></a>_initterm、_initterm_e
查核函式指標的資料表，並將它們初始化的內部方法。  
  
 第一個指標是在資料表中的起始位置，而第二個指標是結束位置。  
  
## <a name="syntax"></a>語法  
  
```  
void __cdecl _initterm(  
   PVFV *,  
   PVFV *  
);  
  
int __cdecl _initterm_e(  
   PVFV *,  
   PVFV *  
);  
```  
  
## <a name="return-value"></a>傳回值  
 如果初始化失敗並擲回錯誤，則傳回非零錯誤碼；若未發生錯誤則為 0。  
  
## <a name="remarks"></a>備註  
 這些方法只會在 C++ 程式初始化期間由內部呼叫。 請勿在程式中呼叫這些方法。  
  
 當這些方法查核函式項目資料表時，會略過 `NULL` 項目並繼續。  
  
## <a name="see-also"></a>請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)