---
title: "_ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbclower
- _ismbclower_l
- _ismbcupper_l
- _ismbcupper
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ismbcupper
- _ismbclower
dev_langs: C++
helpviewer_keywords:
- _ismbcupper function
- ismbclower function
- _ismbclower_l function
- ismbcupper_l function
- _ismbclower function
- ismbcupper function
- ismbclower_l function
- _ismbcupper_l function
ms.assetid: 17d89587-65bc-477c-ba8f-a84e63cf59e7
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b0a94b0d15059c0ecf67a7a33b3be646ed7a2f59
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ismbclower-ismbclowerl-ismbcupper-ismbcupperl"></a>_ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l
檢查多位元組字元是大寫或小寫。  
  
> [!IMPORTANT]
>  這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
int _ismbclower(  
   unsigned int c   
);  
int _ismbclower_l(  
   unsigned int c,  
   _locale_t locale   
);  
int _ismbcupper(  
   unsigned int c   
);  
int _ismbcupper_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>參數  
 `c`  
 待測試字元。  
  
 `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 如果字元符合測試條件，這些常式都會傳回非零值，如果不符合，則傳回 0。 如果 `c` <= 255 且有對應的 `_ismbb` 常式 (例如，`_ismbcalnum` 對應至 `_ismbbalnum`)，結果就是對應之 `_ismbb` 常式的傳回值。  
  
## <a name="remarks"></a>備註  
 這些函式每一個都會測試指定的多位元組字元是否符合指定的條件。  
  
 尾碼為 `_l` 的這些函式版本是一樣的，只不過與地區設定相關的行為使用了傳入的地區設定，而不是目前的地區設定。 如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
|常式|測試條件|字碼頁 932 範例|  
|-------------|--------------------|---------------------------|  
|`_ismbclower`|小寫字母|只有在 `c` 是 ASCII 小寫英文字母的單一位元組表示時，才傳回非零值：0x61<=`c`<=0x7A。|  
|`_ismbclower_l`|小寫字母|只有在 `c` 是 ASCII 小寫英文字母的單一位元組表示時，才傳回非零值：0x61<=`c`<=0x7A。|  
|`_ismbcupper`|大寫字母|只有在 `c` 是 ASCII 大寫英文字母的單一位元組表示時，才傳回非零值：0x41<=`c`<=0x5A。|  
|`_ismbcupper_l`|大寫字母|只有在 `c` 是 ASCII 大寫英文字母的單一位元組表示時，才傳回非零值：0x41<=`c`<=0x5A。|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_ismbclower`|\<mbstring.h>|  
|`_ismbclower_l`|\<mbstring.h>|  
|`_ismbcupper`|\<mbstring.h>|  
|`_ismbcupper_l`|\<mbstring.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [_ismbc 常式](../../c-runtime-library/ismbc-routines.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [is, isw 常式](../../c-runtime-library/is-isw-routines.md)   
 [_ismbb 常式](../../c-runtime-library/ismbb-routines.md)