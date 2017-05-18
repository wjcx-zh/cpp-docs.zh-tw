---
title: setjmp | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- setjmp
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
- setjmp
dev_langs:
- C++
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 602ed9f5b1ff3c809055d9a231f81ee649bab8e8
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="setjmp"></a>setjmp
儲存程式的目前狀態。  
  
## <a name="syntax"></a>語法  
  
```  
int setjmp(  
   jmp_buf env   
);  
```  
  
#### <a name="parameters"></a>參數  
 `env`  
 儲存環境的變數。  
  
## <a name="return-value"></a>傳回值  
 儲存堆疊環境之後，會傳回 0。 如果因 `longjmp` 呼叫而傳回 `setjmp`，則會傳回 `longjmp` 的 `value` 引數，或者，如果 `longjmp` 的 `value` 引數為 0，則 `setjmp` 會傳回 1。 不會傳回錯誤。  
  
## <a name="remarks"></a>備註  
 `setjmp` 函式會使用 `longjmp` 來儲存後續可還原的堆疊環境。 `setjmp` 和 `longjmp` 一起使用時，可提供執行非區域 `goto` 的方式。 它們通常用於將執行控制項傳遞至之前所呼叫常式中的錯誤處理或復原程式碼，而不使用一般呼叫或傳回慣例。  
  
 呼叫 `setjmp` 會在 `env` 中儲存目前堆疊環境。 後續呼叫 `longjmp` 會還原儲存的環境，並將控制權傳給緊接在對應 `setjmp` 呼叫之後的時間點。 接收控制權之常式可存取的所有變數 (暫存器變數除外) 都會包含呼叫 `longjmp` 時所擁有的值。  
  
 可能無法使用 `setjmp` 從機器碼跳到 Managed 程式碼。  
  
 **注意**`setjmp` 和 `longjmp` 不支援 C++ 物件語意。 在 C++ 程式中，使用 C++ 例外狀況處理機制。  
  
 如需詳細資訊，請參閱[使用 setjmp 和 longjmp](../../cpp/using-setjmp-longjmp.md)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`setjmp`|\<setjmp.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 請參閱 [_fpreset](../../c-runtime-library/reference/fpreset.md) 的範例。  
  
## <a name="see-also"></a>另請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [longjmp](../../c-runtime-library/reference/longjmp.md)   
 [_setjmp3](../../c-runtime-library/setjmp3.md)
