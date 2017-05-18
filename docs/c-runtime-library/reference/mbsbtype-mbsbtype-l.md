---
title: "_mbsbtype、_mbsbtype_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsbtype_l
- _mbsbtype
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
- mbsbtype
- mbsbtype_l
- _mbsbtype_l
- _mbsbtype
dev_langs:
- C++
helpviewer_keywords:
- _mbsbtype function
- mbsbtype function
- _mbsbtype_l function
- mbsbtype_l function
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
caps.latest.revision: 19
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 81223356f5dac86fcc161e1c7fd1bc5eb80dcfbf
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="mbsbtype-mbsbtypel"></a>_mbsbtype、_mbsbtype_l
傳回字串中的位元組類型。  
  
> [!IMPORTANT]
>  這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
int _mbsbtype(  
   const unsigned char *mbstr,  
   size_t count   
);  
int _mbsbtype_l(  
   const unsigned char *mbstr,  
   size_t count,  
   _locale_t locale   
);  
```  
  
#### <a name="parameters"></a>參數  
 `mbstr`  
 多位元組字元序列的位址。  
  
 `count`  
 從字串開頭的位元組位移。  
  
 `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 `_mbsbtype`和`_mbsbtype_l`傳回整數值，指出指定的位元組上測試的結果。 下表中的資訊清單常數定義於 Mbctype.h。  
  
|傳回值|位元組類型|  
|------------------|---------------|  
|`_MBC_SINGLE` (0)|單一位元組字元。 例如，在字碼頁 932，`_mbsbtype`傳回 0，如果指定的位元組範圍之內 0x20-0x7E 或 0xA1-0xDF。|  
|`_MBC_LEAD` (1)|多位元組字元的前導位元組。 例如，在字碼頁 932，`_mbsbtype`如果指定的位元組範圍 0x81-0x9F 或 0xE0-內 0xFC 時則傳回 1。|  
|`_MBC_TRAIL` (2)|多位元組字元的後隨位元組。 例如，在字碼頁 932，`_mbsbtype`傳回 2，如果指定的位元組範圍之內 0x40-0x7E 或 0x80-0xFC。|  
|`_MBC_ILLEGAL` (-1)|在 `mbstr` 中位移 `count` 處的位元組之前，找到 `NULL` 字串、無效的字元或 `NULL` 位元組。|  
  
## <a name="remarks"></a>備註  
 `_mbsbtype` 函式會判斷多位元組字元字串中的位元組類型。 此函式只會檢查 `mbstr` 中位移 `count` 處的位元組，而略過指定位元組之前的無效字元。  
  
 輸出值會受到地區設定的 `LC_CTYPE` 分類設定影響；如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 這個沒有 `_l` 後置字元的函式版本，會針對此與地區設定相關的行為使用目前的地區設定；具有 `_l` 後置字元的版本與其相同，只不過它會改用傳入的地區設定參數。 如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 如果輸入字串為 `NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，`errno` 會設為 `EINVAL`，且此函式會傳回 `_MBC_ILLEGAL`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|選擇性標頭|  
|-------------|---------------------|---------------------|  
|`_mbsbtype`|\<mbstring.h>|\<mbctype.h>*|  
|`_mbsbtype_l`|\<mbstring.h>|\<mbctype.h>*|  
  
 \* 適用於作為傳回值使用的資訊清單常數。  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [位元組分類](../../c-runtime-library/byte-classification.md)
