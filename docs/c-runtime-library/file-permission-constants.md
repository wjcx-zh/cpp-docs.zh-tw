---
title: "檔案使用權限常數 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _S_IWRITE
- _S_IREAD
dev_langs:
- C++
helpviewer_keywords:
- S_IWRITE constant
- constants [C++], file attributes
- S_IREAD constant
- file permissions [C++]
- _S_IWRITE constant
- _S_IREAD constant
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
caps.latest.revision: 6
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: fe25cc1ce973d46c87425b59cc2da3544b216033
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="file-permission-constants"></a>檔案使用權限常數
## <a name="syntax"></a>語法  
  
```  
  
#include <sys/stat.h>  
  
```  
  
## <a name="remarks"></a>備註  
 當指定 `_O_CREAT` (`_open`,`_sopen`) 時，需要這些常數的其中之一。  
  
 `pmode` 引數會指定如下所示的檔案使用權限設定。  
  
|常數|意義|  
|--------------|-------------|  
|`_S_IREAD`|允許讀取|  
|`_S_IWRITE`|允許寫入|  
|`_S_IREAD` &#124; `_S_IWRITE`|允許讀取和寫入|  
  
 作為 `_umask` 的 `pmode` 引數時，如下所示的常數會設定使用權限設定。  
  
|常數|意義|  
|--------------|-------------|  
|`_S_IREAD`|不允許寫入 (檔案為唯讀)|  
|`_S_IWRITE`|不允許讀取 (檔案為唯寫)|  
|`_S_IREAD` &#124; `_S_IWRITE`|不允許讀取和寫入|  
  
## <a name="see-also"></a>另請參閱  
 [_open、_wopen](../c-runtime-library/reference/open-wopen.md)   
 [_sopen、_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [_umask](../c-runtime-library/reference/umask.md)   
 [標準類型](../c-runtime-library/standard-types.md)   
 [全域常數](../c-runtime-library/global-constants.md)
