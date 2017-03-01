---
title: feupdateenv | Microsoft Docs
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
- feupdateenv
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
apitype: HeaderDef
f1_keywords:
- feupdateenv
- fenv/feupdateenv
dev_langs:
- C++
helpviewer_keywords:
- feupdateenv function
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
caps.latest.revision: 3
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
ms.openlocfilehash: 170e385a5741ced5612c060a7a537a05b4668432
ms.lasthandoff: 02/24/2017

---
# <a name="feupdateenv"></a>feupdateenv
儲存目前引發的浮點例外狀況、還原指定的浮點環境狀態，然後引發儲存的浮點例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
int feupdateenv(  
   const fenv_t* penv  
);  
```  
  
#### <a name="parameters"></a>參數  
 `penv`  
 `fenv_t` 物件的指標，包含 [fegetenv](http://msdn.microsoft.com/Library/61df848d-6ba8-4c6e-be35-216436fe7736) 或 [feholdexcept](http://msdn.microsoft.com/Library/c286ace3-ec39-482a-be8b-f998d31003d9) 呼叫設定的浮點環境。 您也可以使用 FE_DFL_ENV 巨集指定預設啟動浮點環境。  
  
## <a name="return-value"></a>傳回值  
 如果順利完成所有動作，則傳回 0。        否則，傳回非零值。  
  
## <a name="remarks"></a>備註  
 `feupdateenv` 函式會執行多個動作。 首先，它會將目前引發的浮點例外狀況狀態旗標儲存在自動儲存體中。 然後，它會從儲存在由 `penv` 指向之 `fenv_t` 物件的值中，設定目前的浮點環境。 如果 `penv` 不是 FE_DFL_ENV 或不指向有效的 `fenv_t` 物件，則不定義後續行為。 最後，`feupdateenv` 引發儲存在本機的浮點例外狀況。  
  
 若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。  
  
## <a name="requirements"></a>需求  
  
|函式|C 標頭|C++ 標頭|  
|--------------|--------------|------------------|  
|`feupdateenv`|\<fenv.h>|\<cfenv>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [fegetenv](../../c-runtime-library/reference/fegetenv1.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)
