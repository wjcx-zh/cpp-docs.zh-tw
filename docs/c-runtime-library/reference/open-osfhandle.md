---
title: _open_osfhandle | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _open_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _open_osfhandle
- open_osfhandle
dev_langs:
- C++
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
caps.latest.revision: 11
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 0a201fa08f48198069df26c5c61944c99db73edf
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="openosfhandle"></a>_open_osfhandle
將 C 執行階段檔案描述項與現有的作業系統檔案控制代碼建立關聯。  
  
## <a name="syntax"></a>語法  
  
```  
  
      int _open_osfhandle (  
   intptr_t osfhandle,  
   int flags   
);  
```  
  
#### <a name="parameters"></a>參數  
 `osfhandle`  
 作業系統檔案控制代碼。  
  
 `flags`  
 允許的作業類型。  
  
## <a name="return-value"></a>傳回值  
 如果成功，`_open_osfhandle` 會傳回 C 執行階段檔案描述項。 否則，它會傳回-1。  
  
## <a name="remarks"></a>備註  
 `_open_osfhandle` 函式會配置 C 執行階段檔案描述項，並將它與 `osfhandle` 所指定的作業系統檔案控制代碼建立關聯。 `flags` 引數是整數運算式，由一或多個定義於 Fcntl.h 中的資訊清單常數所組成。 當使用兩個以上的資訊清單常數形成 `flags` 引數時，會使用位元 OR 運算子 (**&#124;**) 結合常數。  
  
 Fcntl.h 定義下列資訊清單常數。  
  
 **_O_APPEND**  
 在每次寫入作業之前，將檔案指標置放到檔案的結尾。  
  
 **_O_RDONLY**  
 開啟檔案為僅供讀取。  
  
 **_O_TEXT**  
 以文字 (已轉譯) 模式開啟檔案。  
  
 **_O_WTEXT**  
 以 Unicode (已轉譯 UTF-16) 模式開啟檔案。  
  
 若要關閉以 `_open_osfhandle` 開啟的檔案，請呼叫 `_close`。 呼叫 `_close` 也會關閉基礎控制代碼，因此不必在原始控制代碼上呼叫 Win32 函式 `CloseHandle`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_open_osfhandle`|\<io.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>另請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)
