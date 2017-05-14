---
title: _setmbcp | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _setmbcp
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
- _setmbcp
- setmbcp
dev_langs:
- C++
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
caps.latest.revision: 13
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 4ae4dc9b57da5ee7d38f32066b8b4b204c50f065
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="setmbcp"></a>_setmbcp
設定新的多位元組字碼頁。  
  
## <a name="syntax"></a>語法  
  
```  
int _setmbcp(  
   int codepage   
);  
```  
  
#### <a name="parameters"></a>參數  
 `codepage`  
 與地區設定無關之多位元組常式的新字碼頁設定。  
  
## <a name="return-value"></a>傳回值  
 如果成功設定字碼頁，則會傳回 0。 如果不正確的字碼頁值提供給`codepage`，傳回-1 和字碼頁設定為不變。 如果記憶體配置失敗，則會將 `errno` 設為 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 `_setmbcp` 函式指定新的多位元組字碼頁。 根據預設，執行階段系統會自動將多位元組字碼頁設定為系統預設的 ANSI 字碼頁。 多位元組字碼頁設定會影響所有與地區設定無關的多位元組常式。 不過，可能會指示 `_setmbcp` 使用針對目前地區設定所定義的字碼頁 (請參閱下列資訊清單常數和相關聯行為結果的清單)。 如需依存於地區設定字碼頁而非多位元組字碼頁的多位元組常式清單，請參閱[解譯多位元組字元序列](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)。  
  
 多位元組字碼頁也會影響下列執行階段程式庫常式的多位元組字元處理︰  
  
||||  
|-|-|-|  
|[_exec 函式](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](../../c-runtime-library/reference/mktemp-wmktemp.md)|[_stat](../../c-runtime-library/reference/stat-functions.md)|  
|[_fullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)|[_spawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
|[_makepath](../../c-runtime-library/reference/makepath-wmakepath.md)|[_splitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)|[tmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
  
 此外，接收多位元組字元 `argv` 或 `envp` 程式引數作為參數的所有執行階段程式庫常式引數 (例如 `_exec` 和 `_spawn` 系列) 都是根據多位元組字碼頁來處理這些字串。 因此，變更多位元組字碼頁的 `_setmbcp` 呼叫也會影響這些常式。  
  
 `codepage` 引數可以設為下列任何一個值：  
  
-   `_MB_CP_ANSI` 在程式啟動時，使用從作業系統取得的 ANSI 字碼頁。  
  
-   `_MB_CP_LOCALE` 使用從先前 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 呼叫取得的目前地區設定字碼頁。  
  
-   `_MB_CP_OEM` 在程式啟動時，使用從作業系統取得的 OEM 字碼頁。  
  
-   `_MB_CP_SBCS` 使用單一位元組字碼頁。 字碼頁設定為 `_MB_CP_SBCS` 時，[_ismbblead](../../c-runtime-library/reference/ismbblead-ismbblead-l.md) 這類常式一律會傳回 false。  
  
-   任何其他有效字碼頁值，不論值是 ANSI、OEM 或其他作業系統支援的字碼頁 (但不支援的 UTF-7 和 UTF-8 除外)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_setmbcp`|\<mbctype.h>|  
  
 如需相容性詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)
