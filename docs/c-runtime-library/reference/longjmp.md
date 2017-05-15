---
title: longjmp | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- longjmp
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
- longjmp
dev_langs:
- C++
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: b5af03e83cc39c20fca310ba0c2377469c59ef38
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="longjmp"></a>longjmp
還原堆疊環境和執行地區設定。  
  
## <a name="syntax"></a>語法  
  
```  
  
      void longjmp(  
   jmp_buf env,  
   int value   
);  
```  
  
#### <a name="parameters"></a>參數  
 `env`  
 儲存環境的變數。  
  
 *value*  
 要傳回至 `setjmp` 呼叫的值。  
  
## <a name="remarks"></a>備註  
 `longjmp` 函式會還原之前由 `setjmp` 儲存在 `env` 中的堆疊環境和執行地區設定。 `setjmp` 和 `longjmp` 可讓您執行非區域 `goto`；它們通常用於將執行控制項傳遞至之前所呼叫常式中的錯誤處理或復原程式碼，而不使用標準呼叫和傳回慣例。  
  
 呼叫 `setjmp` 會在 `env` 中儲存目前的堆疊環境。 後續呼叫 `longjmp` 會還原儲存的環境，並將控制權還給緊接在對應 `setjmp` 呼叫之後的時間點。 執行會繼續，就像是 `setjmp` 呼叫剛傳回 *value* 一樣。 接收控制項的常式可存取之所有變數 (暫存器變數除外) 的值會包含呼叫 `longjmp` 時所擁有的值。 無法預測暫存器變數的值。 `setjmp` 所傳回的值必須為非零。 如果傳遞的 *value* 為 0，實際傳回時會以值 1 替代。  
  
 請在所呼叫 `setjmp` 傳回的函式之前呼叫 `longjmp`，否則會出現無法預期的結果。  
  
 使用 `longjmp` 時，請注意下列限制：  
  
-   請勿假設暫存器變數的值將保持不變。 執行 `longjmp` 之後，可能無法將呼叫 `setjmp` 之常式中的暫存器變數值還原為適當的值。  
  
-   請勿使用 `longjmp` 將控制項移出中斷處理常式，除非中斷是由浮點例外狀況所造成。 在此情況下，如果藉由呼叫 `_fpreset` 先將浮點數學封裝重新初始化，則可能會透過 `longjmp` 從中斷處理常式傳回一個程式。  
  
     **注意**：請在 C++ 程式中小心使用 `setjmp` 和 `longjmp`。 因為這些函式不支援 C++ 物件語意，所以使用 C++ 例外狀況處理機制會更安全。  
  
 如需詳細資訊，請參閱[使用 setjmp/longjmp](../../cpp/using-setjmp-longjmp.md)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`longjmp`|\<setjmp.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
 請參閱 [_fpreset](../../c-runtime-library/reference/fpreset.md) 的範例。  
  
## <a name="see-also"></a>另請參閱  
 [處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [setjmp](../../c-runtime-library/reference/setjmp.md)
