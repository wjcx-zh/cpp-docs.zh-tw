---
title: "_putenv、_wputenv | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _putenv
- _wputenv
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tputenv
- _wputenv
- _putenv
- wputenv
- tputenv
dev_langs:
- C++
helpviewer_keywords:
- _putenv function
- environment variables, deleting
- putenv function
- tputenv function
- environment variables, creating
- wputenv function
- _wputenv function
- _tputenv function
- environment variables, modifying
ms.assetid: 9ba9b7fd-276e-45df-8420-d70c4204b8bd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 12b1379ea70c841f1689a8b83fae7ca7f43f5789
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="putenv-wputenv"></a>_putenv、_wputenv
建立、修改或移除環境變數。 這些函式已有更安全的版本可用，請參閱 [_putenv_s、_wputenv_s](../../c-runtime-library/reference/putenv-s-wputenv-s.md)。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱[通用 Windows 平台應用程式不支援 CRT 函式](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。  
  
## <a name="syntax"></a>語法  
  
```  
int _putenv(  
   const char *envstring   
);  
int _wputenv(  
   const wchar_t *envstring   
);  
```  
  
#### <a name="parameters"></a>參數  
 `envstring`  
 環境字串定義。  
  
## <a name="return-value"></a>傳回值  
 傳回 0，如果成功則為-1 在錯誤的情況下。  
  
## <a name="remarks"></a>備註  
 `_putenv` 函式會加入新的環境變數，或修改現有環境變數的值。 環境變數會定義處理序所執行的環境 (例如，要與程式連結之程式庫的預設搜尋路徑)。 `_wputenv` 是寬字元版本的 `_putenv`；`envstring` 的 `_wputenv` 引數是寬字元字串。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tputenv`|`_putenv`|`_putenv`|`_wputenv`|  
  
 `envstring` 引數必須是 `varname=string` 格式的字串指標，其中 `varname` 是要新增或修改之環境變數的名稱，而 `string` 是變數的值。 如果 `varname` 已是環境的一部分，則其值會取代為 `string`；否則會新增 `varname` 變數及其 `string` 值至環境。 您可以指定空的 `string` (也就是只指定 `varname=`)，以從環境移除變數。  
  
 `_putenv` 和 `_wputenv` 只會影響目前處理序的本機環境；您無法使用它們來修改命令層級環境。 換句話說，這些函式只會在執行階段程式庫可以存取的資料結構上運作，而不會在作業系統為某個處理序所建立的環境區段上運作。 目前處理序終止時，環境會還原為呼叫處理序層級 (在大部分情況下是作業系統層級)。 不過，修改過的環境可以傳遞至 `_spawn`、`_exec` 或 `system` 所建立的任何新處理序，而這些新的處理序會取得 `_putenv` 和 `_wputenv` 所新增的任何項目。  
  
 請不要直接變更環境項目，而是使用 `_putenv` 或 `_wputenv` 進行變更。 特別的是，直接釋出 `_environ[]` 全域陣列的元素可能會造成需要處理的無效記憶體。  
  
 `getenv` 和 `_putenv` 使用全域變數 `_environ` 來存取環境資料表；`_wgetenv` 和 `_wputenv` 使用 `_wenviron`。 `_putenv` 和`_wputenv`可能的值變更`_environ`和`_wenviron`，因此失效`_envp`引數`main`和`_wenvp`引數`wmain`。 因此，較安全的作法是使用 `_environ` 或 `_wenviron` 來存取環境資訊。 如需 `_putenv` 和 `_wputenv` 與全域變數之關聯的詳細資訊，請參閱 [_environ、_wenviron](../../c-runtime-library/environ-wenviron.md)。  
  
> [!NOTE]
>  `_putenv` 和 `_getenv` 系列的函式不是安全執行緒。 `_putenv` 正在修改字串時，`_getenv` 可能會傳回字串指標，因而導致隨機失敗。 確定這些函式的呼叫已同步。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_putenv`|\<stdlib.h>|  
|`_wputenv`|\<stdlib.h> 或 \<wchar.h>|  
  
 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 如需如何使用 `_putenv` 的範例，請參閱 [getenv、_wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)。  
  
## <a name="see-also"></a>請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [getenv、_wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [_searchenv、_wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)