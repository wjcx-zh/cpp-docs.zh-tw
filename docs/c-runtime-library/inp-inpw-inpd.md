---
title: "_inp、_inpw、_inpd | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _inp
- _inpw
- _inpd
apilocation:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- inpd
- _inp
- _inpw
- _inpd
dev_langs:
- C++
helpviewer_keywords:
- inp function
- inpw function
- ports, I/O routines
- inpd function
- _inp function
- _inpd function
- I/O [CRT], port
- _inpw function
ms.assetid: 5d9c2e38-fc85-4294-86d5-7282cc02d1b3
caps.latest.revision: 16
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
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 54325f60b0d1714cab68f17152609a8980bc2a60

---
# <a name="inp-inpw-inpd"></a>_inp、_inpw、_inpd
從連接埠輸入一個位元組 (`_inp`)、一個字組 (`_inpw`) 或雙字組 (`_inpd`)。  
  
> [!IMPORTANT]
>  這些函式已被取代。 自 Visual Studio 2015 起，這些函式即無法在 CRT 中使用。  
  
> [!IMPORTANT]
>  這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
int _inp(   
   unsigned short port   
);  
unsigned short _inpw(   
   unsigned short port   
);  
unsigned long _inpd(   
   unsigned short port   
);  
```  
  
#### <a name="parameters"></a>參數  
 `port`  
 I/O 連接埠號碼。  
  
## <a name="return-value"></a>傳回值  
 這些函式會傳回從 `port`讀取而來的位元組、字組或雙字組。 不會傳回錯誤。  
  
## <a name="remarks"></a>備註  
 `_inp`、 `_inpw`及 `_inpd` 函式會從指定的輸入連接埠讀取位元組、字組及雙字組。 輸入的值可以是 0-65535 之間任何不帶正負號的短整數。  
  
 因為這些函式會直接讀取 I/O 連接埠，所以無法在 Windows NT、 Windows 2000、Windows XP 及 Windows Server 2003 的使用者程式碼中使用。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_inp`|\<conio.h>|  
|`_inpw`|\<conio.h>|  
|`_inpd`|\<conio.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../c-runtime-library/crt-library-features.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [主控台和連接埠 I/O](../c-runtime-library/console-and-port-i-o.md)   
 [_outp、_outpw、_outpd](../c-runtime-library/outp-outpw-outpd.md)


<!--HONumber=Feb17_HO4-->


