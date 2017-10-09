---
title: _CxxThrowException | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CxxThrowException
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
- CxxThrowException
- _CxxThrowException
dev_langs:
- C++
helpviewer_keywords:
- _CxxThrowException function
- CxxThrowException function
ms.assetid: 0b90bef5-b7d2-46e0-88e2-59e531e01a4d
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 5cfe894dc20e77bf34067c16fddd74432c522bda
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="cxxthrowexception"></a>_CxxThrowException
建立例外狀況記錄，並呼叫執行階段環境以開始處理例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
extern "C" void __stdcall _CxxThrowException(  
   void* pExceptionObject  
   _ThrowInfo* pThrowInfo  
);  
```  
  
#### <a name="parameters"></a>參數  
 [in] `pExceptionObject`  
 產生例外狀況的物件。  
  
 [in] `pThrowInfo`  
 處理例外狀況所需的資訊。  
  
## <a name="remarks"></a>備註  
 此方法包含在編譯器用來處理例外狀況的僅限編譯器檔案中。 請勿從您的程式碼直接呼叫此方法。  
  
## <a name="requirements"></a>需求  
 **來源︰**Throw.cpp  
  
## <a name="see-also"></a>另請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)
