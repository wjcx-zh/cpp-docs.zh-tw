---
title: "_putenv_s、_wputenv_s | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wputenv_s
- _putenv_s
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
- putenv_s
- wputenv_s
- _wputenv_s
- _putenv_s
dev_langs:
- C++
helpviewer_keywords:
- wputenv_s function
- _putenv_s function
- environment variables, deleting
- putenv_s function
- _wputenv_s function
- environment variables, creating
- environment variables, modifying
ms.assetid: fbf51225-a8da-4b9b-9d7c-0b84ef72df18
caps.latest.revision: 20
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
ms.openlocfilehash: fc06fd348f1fce9e9eb9fe36bc976460fc57d884
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="putenvs-wputenvs"></a>_putenv_s、_wputenv_s
建立、修改或移除環境變數。 這些是 [_putenv、_wputenv](../../c-runtime-library/reference/putenv-wputenv.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/en-us/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t _putenv_s(  
   const char *name,  
   const char *value   
);  
errno_t _wputenv_s(  
   const wchar_t *name,  
   const wchar_t *value  
);  
```  
  
#### <a name="parameters"></a>參數  
 `name`  
 環境變數名稱。  
  
 `value`  
 要設定的環境變數值。  
  
## <a name="return-value"></a>傳回值  
 如果成功則為 0，否則為錯誤碼。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|`name`|`value`|傳回值|  
|------------|-------------|------------------|  
|`NULL`|任何|`EINVAL`|  
|任何|`NULL`|`EINVAL`|  
  
 如果發生其中一種錯誤狀況，這些函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回 `EINVAL`，並將 `errno` 設為 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 `_putenv_s` 函式會加入新的環境變數，或修改現有環境變數的值。 環境變數會定義處理序所執行的環境 (例如，要與程式連結之程式庫的預設搜尋路徑)。 `_wputenv_s` 是寬字元版本的 `_putenv_s`；`envstring` 的 `_wputenv_s` 引數是寬字元字串。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tputenv_s`|`_putenv_s`|`_putenv_s`|`_wputenv_s`|  
  
 `name` 是要加入或修改之環境變數的名稱，而 `value` 是變數的值。 如果 `name` 已是環境的一部分，則其值會取代為 `value`；否則新 `name` 變數和其 `value` 會加入環境。 針對 `value` 指定空字串 (即 "")，即可從環境移除變數。  
  
 `_putenv_s` 和 `_wputenv_s` 只會影響目前處理序的本機環境；您無法使用它們來修改命令層級環境。 這些函式只會在執行階段程式庫可以存取的資料結構上運作，而不會在作業系統為某個處理序所建立的環境「區段」上運作。 目前處理序終止時，環境會還原為呼叫處理序層級，而這在大部分情況下是作業系統層級。 不過，修改過的環境可以傳遞至 `_spawn`、`_exec` 或 `system` 所建立的任何新處理序，而這些新的處理序會取得 `_putenv_s` 和 `_wputenv_s` 所加入的任何新項目。  
  
 請不要直接變更環境項目；而是使用 `_putenv_s` 或 `_wputenv_s` 進行變更。 特別的是，直接釋出 `_environ[]` 全域陣列的項目可能會造成需要處理的無效記憶體。  
  
 `getenv` 和 `_putenv_s` 使用全域變數 `_environ` 來存取環境資料表；`_wgetenv` 和 `_wputenv_s` 使用 `_wenviron`。 `_putenv_s` 和 `_wputenv_s` 可能會變更 `_environ` 和 `_wenviron` 的值，進而讓 `main` 的 `envp` 引數和 `wmain` 的 `_wenvp` 引數失效。 因此，較安全的作法是使用 `_environ` 或 `_wenviron` 來存取環境資訊。 如需 `_putenv_s` 和 `_wputenv_s` 與全域變數之關聯性的詳細資訊，請參閱 [_environ、_wenviron](../../c-runtime-library/environ-wenviron.md)。  
  
> [!NOTE]
>  `_putenv_s` 和 `_getenv_s` 系列的函式不是安全執行緒。 `_putenv_s` 正在修改字串時，`_getenv_s` 可能會傳回字串指標，因而導致隨機失敗。 確定這些函式的呼叫已同步。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_putenv_s`|\<stdlib.h>|  
|`_wputenv_s`|\<stdlib.h> 或 \<wchar.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 如需示範如何使用 `_putenv_s` 的範例，請參閱 [getenv_s、_wgetenv_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md)。  
  
## <a name="see-also"></a>另請參閱  
 [處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [getenv、_wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [_searchenv、_wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)
