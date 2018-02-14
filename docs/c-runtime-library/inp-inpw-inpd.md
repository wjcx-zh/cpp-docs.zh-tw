---
title: "_inp、_inpw、_inpd | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7b73d8287954a401b8b966fb1220cfcecfc416eb
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="inp-inpw-inpd"></a>_inp、_inpw、_inpd
從連接埠輸入一個位元組 (`_inp`)、一個字組 (`_inpw`) 或雙字組 (`_inpd`)。  
  
> [!IMPORTANT]
>  這些函式已被取代。 自 Visual Studio 2015 起，這些函式即無法在 CRT 中使用。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
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
 `_inp`、 `_inpw`及 `_inpd` 函式會從指定的輸入連接埠讀取位元組、字組及雙字組。 輸入的值可以是 0 - 65535 之間任何不帶正負號的 short 整數。  
  
 由於這些函式直接從 I/O 連接埠讀取，因此無法用於使用者程式碼。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_inp`|\<conio.h>|  
|`_inpw`|\<conio.h>|  
|`_inpd`|\<conio.h>|  
  
 如需相容性的詳細資訊，請參閱 [相容性](../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>請參閱  
 [主控台和連接埠 I/O](../c-runtime-library/console-and-port-i-o.md)   
 [_outp、_outpw、_outpd](../c-runtime-library/outp-outpw-outpd.md)