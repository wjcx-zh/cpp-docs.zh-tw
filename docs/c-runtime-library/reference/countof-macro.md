---
title: _countof Macro | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
- _countof
- countof
dev_langs:
- C++
helpviewer_keywords:
- countof macro
- _countof macro
ms.assetid: 86198767-f7e5-4beb-898d-3cbbf60350a3
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 71d4310525f1d96184749b5b0b24cb0cf1da8512
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="countof-macro"></a>_countof 巨集
計算靜態配置陣列中的元素數目。  
  
## <a name="syntax"></a>語法  
  
```  
size_t _countof(   
   array  
);  
```  
  
#### <a name="parameters"></a>參數  
 `array`  
 陣列的名稱。  
  
## <a name="return-value"></a>傳回值  
 陣列中的元素數目，表示為 `size_t`。  
  
## <a name="remarks"></a>備註  
 請確定 `array` 實際上是陣列，而不是指標。 在 C 中，如果 `array` 是指標，則 `_countof` 將產生錯誤的結果。 在 C++ 中，如果 `array` 是指標，則 `_countof` 將無法編譯。  
  
## <a name="requirements"></a>需求  
  
|巨集|必要的標頭|  
|-----------|---------------------|  
|`_countof`|\<stdlib.h>|  
  
## <a name="example"></a>範例  
  
```  
// crt_countof.cpp  
#define _UNICODE  
#include <stdio.h>  
#include <stdlib.h>  
#include <tchar.h>  
  
int main( void )  
{  
   _TCHAR arr[20], *p;  
   printf( "sizeof(arr) = %zu bytes\n", sizeof(arr) );  
   printf( "_countof(arr) = %zu elements\n", _countof(arr) );  
   // In C++, the following line would generate a compile-time error:  
   // printf( "%zu\n", _countof(p) ); // error C2784 (because p is a pointer)  
  
   _tcscpy_s( arr, _countof(arr), _T("a string") );  
   // unlike sizeof, _countof works here for both narrow- and wide-character strings  
}  
```  
  
```Output  
sizeof(arr) = 40 bytes  
_countof(arr) = 20 elements  
```  
  
## <a name="see-also"></a>另請參閱  
 [sizeof 運算子](../../cpp/sizeof-operator.md)
