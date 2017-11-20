---
title: "_get_purecall_handler、_set_purecall_handler | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _set_purecall_handler
- _set_purecall_handler_m
- _get_purecall_handler
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
- _set_purecall_handler
- _set_purecall_handler_m
- set_purecall_handler_m
- set_purecall_handler
- stdlib/_set_purecall_handler
- stdlib/_get_purecall_handler
- _get_purecall_handler
dev_langs: C++
helpviewer_keywords:
- _set_purecall_handler function
- set_purecall_handler function
- purecall_handler
- set_purecall_handler_m function
- _purecall_handler
- _set_purecall_handler_m function
- _get_purecall_handler function
ms.assetid: 2759b878-8afa-4129-86e7-72afc2153d9c
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b32cf4e20be739f712cb9c0b0e0c8d3b0f0792ad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="getpurecallhandler-setpurecallhandler"></a>_get_purecall_handler、_set_purecall_handler
取得或設定純虛擬函式呼叫的錯誤處理常式。  
  
## <a name="syntax"></a>語法  
  
```  
typedef void (__cdecl* _purecall_handler)(void);  
  
_purecall_handler __cdecl _get_purecall_handler(void);  
  
_purecall_handler __cdecl _set_purecall_handler(   
   _purecall_handler function  
);  
```  
  
#### <a name="parameters"></a>參數  
 `function`  
 呼叫純虛擬函式時要呼叫的函式。 `_purecall_handler` 函式必須具有 void 傳回類型。  
  
## <a name="return-value"></a>傳回值  
 上一個 `_purecall_handler`。 若無上一個處理常式，則傳回 `nullptr`。  
  
## <a name="remarks"></a>備註  
 `_get_purecall_handler` 和 `_set_purecall_handler` 函式是 Microsoft 專有而且僅適用於 C++ 程式碼。  
  
 呼叫純虛擬函式會產生錯誤，因為它有沒有實作。 根據預設，呼叫純虛擬函式時，編譯器會產生程式碼來叫用錯誤處理常式函式，該函式會終止程式。 您可以為純虛擬函式呼叫安裝您自己的錯誤處理常式函式，以攔截它們，用於偵錯或報告目的。 若要使用您自己的錯誤處理常式，建立具有 `_purecall_handler` 簽章的函式，然後使用 `_set_purecall_handler` 使其成為目前的處理常式。  
  
 因為每個處理序只有一個 `_purecall_handler`，當您呼叫 `_set_purecall_handler` 時，它立即影響所有執行緒。 任何執行緒的上一個呼叫端會設定處理常式。  
  
 若要還原預設行為，請使用 `nullptr` 引數呼叫 `_set_purecall_handler`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_get_purecall_handler`, `_set_purecall_handler`|\<cstdlib> 或 \<stdlib.h>|  
  
 如需相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// _set_purecall_handler.cpp  
// compile with: /W1  
#include <tchar.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
class CDerived;  
class CBase  
{  
public:  
   CBase(CDerived *derived): m_pDerived(derived) {};  
   ~CBase();  
   virtual void function(void) = 0;  
  
   CDerived * m_pDerived;  
};  
  
class CDerived : public CBase  
{  
public:  
   CDerived() : CBase(this) {};   // C4355  
   virtual void function(void) {};  
};  
  
CBase::~CBase()  
{  
   m_pDerived -> function();  
}  
  
void myPurecallHandler(void)  
{  
   printf("In _purecall_handler.");  
   exit(0);  
}  
  
int _tmain(int argc, _TCHAR* argv[])  
{  
   _set_purecall_handler(myPurecallHandler);  
   CDerived myDerived;  
}  
```  
  
```Output  
In _purecall_handler.  
```  
  
## <a name="see-also"></a>另請參閱  
 [錯誤處理](../../c-runtime-library/error-handling-crt.md)   
 [_purecall](../../c-runtime-library/reference/purecall.md)