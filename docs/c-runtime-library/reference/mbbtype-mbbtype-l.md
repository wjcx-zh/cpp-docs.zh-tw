---
title: "_mbbtype、_mbbtype_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbbtype
- _mbbtype_l
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
- _mbbtype_l
- mbbtype
- mbbtype_l
- _mbbtype
dev_langs: C++
helpviewer_keywords:
- _mbbtype function
- _mbbtype_l function
- mbbtype function
- mbbtype_l function
ms.assetid: b8e34b40-842a-4298-aa39-0bd2d8e51c2a
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ae66b1c0765f496dcfe460c4ea7ff4f84e9333ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mbbtype-mbbtypel"></a>_mbbtype、_mbbtype_l
根據上一個位元組傳回位元組類型。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
int _mbbtype(  
   unsigned char c,  
   int type   
);  
int _mbbtype_l(  
   unsigned char c,  
   int type,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>參數  
 `c`  
 要測試的字元。  
  
 `type`  
 要測試的位元組類型。  
  
 `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 `_mbbtype` 傳回字串中的位元組類型。 這項決策是即時線上的，如提供控制項測試條件的 `type` 值所指定。 `type` 是該字串中前一個位元組的類型。 下表中的資訊清單常數定義於 Mbctype.h。  
  
|`type` 的值|`_mbbtype` 測試|傳回值|`c`|  
|---------------------|--------------------------|------------------|---------|  
|1 以外的任何值|有效的單一位元組或前導位元|`_MBC_SINGLE` (0)|單一位元組 (0x20-0x7E、 0xA1-0xDF)|  
|1 以外的任何值|有效的單一位元組或前導位元|`_MBC_LEAD` (1)|多位元組字元的前導位元組 (0x81-0x9F、 0xE0-0xFC)|  
|1 以外的任何值|有效的單一位元組或前導位元|`_MBC_ILLEGAL`<br /><br /> ( -1)|無效的字元 (任何值除了 0x20-0x7E、 0xA1-0xDF、 0x81-0x9F、 0xE0-0xFC|  
|1|有效的後隨位元組|`_MBC_TRAIL` (2)|結尾的多位元組字元位元組 (0x40-0x7E、 0x80-0xFC)|  
|1|有效的後隨位元組|`_MBC_ILLEGAL`<br /><br /> ( -1)|無效的字元 (任何值除了 0x20-0x7E、 0xA1-0xDF、 0x81-0x9F、 0xE0-0xFC|  
  
## <a name="remarks"></a>備註  
 `_mbbtype` 函式會判斷多位元組字元中的位元組類型。 如果 `type` 的值為 1 以外的任何值，則 `_mbbtype` 會針對多位元組字元之有效的單一位元組或前導位元組進行測試。 如果 `type` 的值為 1，則 `_mbbtype` 會針對多位元組字元之有效的後隨位元組進行測試。  
  
 輸出值會受到地區設定的 `LC_CTYPE` 分類設定影響；如需詳細資訊，請參閱 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 這個函式的 `_mbbtype` 版本會針對地區設定相關的行為使用目前的地區設定；而 `_mbbtype_l` 版本也一樣，除了改用傳入的地區設定以外。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。  
  
 在舊版中，`_mbbtype` 名為 `chkctype`。 對於新的程式碼，請改用 `_mbbtype`。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|選擇性標頭|  
|-------------|---------------------|---------------------|  
|`_mbbtype`|\<mbstring.h>|\<mbctype.h>*|  
|`_mbbtype_l`|\<mbstring.h>|\<mbctype.h>*|  
  
 \* 針對可作為傳回值使用之資訊清單常數的定義。  
  
 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [位元組分類](../../c-runtime-library/byte-classification.md)