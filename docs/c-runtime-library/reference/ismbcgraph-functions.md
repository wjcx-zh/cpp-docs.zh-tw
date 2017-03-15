---
title: "_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbcpunct_l
- _ismbcblank
- _ismbcprint
- _ismbcgraph_l
- _ismbcblank_l
- _ismbcpunct
- _ismbcprint_l
- _ismbcspace_l
- _ismbcspace
- _ismbcgraph
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
- _ismbcspace
- _ismbcgraph
- _ismbcpunct
- ismbcspace_l
- ismbcgraph
- _ismbcgraph_l
- _ismbcprint
- _ismbcspace_l
- ismbcprint
- ismbcgraph_l
- ismbcspace
- ismbcpunct
dev_langs:
- C++
helpviewer_keywords:
- ismbcspace_l function
- _ismbcprint_l function
- ismbcspace function
- ismbcpunct function
- _ismbcspace_l function
- _ismbcprint function
- ismbcprint function
- _ismbcgraph function
- ismbcgraph_l function
- _ismbcpunct_l function
- ismbcpunct_l function
- ismbcprint_l function
- _ismbcpunct function
- ismbcgraph function
- _ismbcgraph_l function
- _ismbcspace function
ms.assetid: 8e0a5f47-ba64-4411-92a3-3c525d16e3be
caps.latest.revision: 21
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: eeeab09167f3330ab06dc664fd0163206b6b6ff8
ms.lasthandoff: 02/24/2017

---
# <a name="ismbcgraph-ismbcgraphl-ismbcprint-ismbcprintl-ismbcpunct-ismbcpunctl-ismbcblank-ismbcblankl-ismbcspace-ismbcspacel"></a>_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l
判斷字元是否為圖形字元、顯示字元、標點符號字元或空白字元。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援的 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
int _ismbcgraph(  
   unsigned int c   
);  
int _ismbcgraph_l(  
   unsigned int c,  
   _locale_t locale   
);  
int _ismbcprint(  
   unsigned int c   
);  
int _ismbcprint_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcpunct(  
   unsigned int c  
);  
int _ismbcpunct_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcblank(  
   unsigned int c   
);  
int _ismbcblank_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcspace(  
   unsigned int c   
);  
int _ismbcspace_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>參數  
 `c`  
 需要判斷的字元。  
  
 `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 如果字元符合測試條件，這些常式都會傳回非零值，如果不符合，則傳回 0。 如果`c` <= 255 且有對應的 `_ismbb` 常式 (例如，`_ismbcalnum` 對應至 `_ismbbalnum`)，結果就是對應之 `_ismbb` 常式的傳回值。  
  
 這些函式版本都完全相同，除了具有 `_l` 尾碼的函式會使用傳入的地區設定參數來處理地區設定相關行為，而不使用目前的地區設定。 如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
## <a name="remarks"></a>備註  
 這些函式每一個都會測試指定的多位元組字元是否符合指定的條件。  
  
|常式|測試條件|字碼頁 932 範例|  
|-------------|--------------------|---------------------------|  
|`_ismbcgraph`|圖形|只有在 `c` 代表單一位元組，除了空白字元 ( ) 以外的任何 ASCII 或片假名可列印字元時，才傳回非零。|  
|`_ismbcprint`|可列印|只有在 `c` 代表單一位元組，包括空白字元 ( ) 在內的任何 ASCII 或片假名可列印字元時，才傳回非零。|  
|`_ismbcpunct`|標點符號|只有在 `c` 是代表任何 ASCII 或片假名標點符號字元的單一位元組時，才傳回非零。|  
|`_ismbcblank`|空格或水平索引標籤|只有在 `c` 是空格或水平索引標籤字元時，才傳回非零︰`c`=0x20 或 `c`=0x09。|  
|`_ismbcspace`|空白字元|只有在 `c` 是空白字元時，才傳回非零︰`c`=0x20 或 0x09<=`c`<=0x0D。|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_ismbcgraph`|\<mbstring.h>|  
|`_ismbcgraph_l`|\<mbstring.h>|  
|`_ismbcprint`|\<mbstring.h>|  
|`_ismbcprint_l`|\<mbstring.h>|  
|`_ismbcpunct`|\<mbstring.h>|  
|`_ismbcpunct_l`|\<mbstring.h>|  
|`_ismbcblank`|\<mbstring.h>|  
|`_ismbcblank_l`|\<mbstring.h>|  
|`_ismbcspace`|\<mbstring.h>|  
|`_ismbcspace_l`|\<mbstring.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
  
-   [System::Char::IsPunctuation](https://msdn.microsoft.com/en-us/library/system.char.ispunctuation.aspx)  
  
-   [System::Char::IsWhiteSpace](https://msdn.microsoft.com/en-us/library/system.char.iswhitespace.aspx)  
  
-   對`_ismbcgraph` 和 `_ismbcprint`︰不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_ismbc 常式](../../c-runtime-library/ismbc-routines.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)   
 [_ismbb 常式](../../c-runtime-library/ismbb-routines.md)
