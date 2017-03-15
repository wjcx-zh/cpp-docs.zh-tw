---
title: feholdexcept2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- feholdexcept
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
- feholdexcept
- fenv/feholdexcept
dev_langs:
- C++
helpviewer_keywords:
- feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 40c56f3ebd01ac809b48c48dcda85ef8a3217be4
ms.lasthandoff: 02/24/2017

---
# <a name="feholdexcept"></a>feholdexcept
將目前的浮點環境儲存在指定的物件中、清除浮點狀態旗標，以及可能的話，將浮點環境放入連續模式中。  
  
## <a name="syntax"></a>語法  
  
```  
int feholdexcept(  
   fenv_t *penv  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 `penv`  
 `fenv_t` 物件的指標，包含浮點環境複本。  
  
## <a name="return-value"></a>傳回值  
 如果且只有在函式能夠順利開啟連續浮點例外狀況處理時，才傳回零。  
  
## <a name="remarks"></a>備註  
 `feholdexcept` 函式用來將目前浮點環境的狀態儲存在由 `penv` 指向的 `fenv_t` 物件中，並將環境設定為不會因浮點例外狀況而中斷執行。 這稱之為連續模式。  此模式會繼續執行，直到使用 [fesetenv](http://msdn.microsoft.com/Library/a34b2705-0bd4-452e-a30f-eea3898d8183) 或 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md) 還原環境為止。  
  
 您可以在需要隱藏呼叫端一或多個浮點例外狀況的副程式開頭使用此函式。 若要報告例外狀況，您只要使用 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md) 清除不想要的例外狀況，然後呼叫 `feupdateenv` 即可結束連續模式。  
  
 若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。  
  
## <a name="requirements"></a>需求  
  
|函式|C 標頭|C++ 標頭|  
|--------------|--------------|------------------|  
|`feholdexcept`|\<fenv.h>|\<cfenv>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [fesetenv](http://msdn.microsoft.com/Library/a34b2705-0bd4-452e-a30f-eea3898d8183)   
 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md)
