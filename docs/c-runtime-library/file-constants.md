---
title: 檔案常數 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _O_EXCL
- _O_RDWR
- _O_APPEND
- _O_RDONLY
- _O_TRUNC
- _O_CREAT
- _O_WRONLY
dev_langs:
- C++
helpviewer_keywords:
- _O_RDWR constant
- O_EXCL constant
- O_RDWR constant
- O_WRONLY constant
- O_APPEND constant
- O_CREAT constant
- _O_CREAT constant
- _O_APPEND constant
- _O_EXCL constant
- O_TRUNC constant
- _O_RDONLY constant
- _O_TRUNC constant
- O_RDONLY constant
- _O_WRONLY constant
ms.assetid: c8fa5548-9ac2-4217-801d-eb45e86f2fa4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31d6deadb3d7cae7ed8717056b632cd46fa79370
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389711"
---
# <a name="file-constants"></a>檔案常數
## <a name="syntax"></a>語法  
  
```  
  
#include <fcntl.h>  
  
```  
  
## <a name="remarks"></a>備註  
 整數運算式是由這些常數其中的一或多個常數所組成，可決定允許的讀取或寫入作業類型。 它是透過一或多個常數與轉譯模式常數的結合所組成。  
  
 檔案常數如下：  
  
 `_O_APPEND`  
 在每次寫入作業之前，將檔案指標重新置放到檔案的結尾。  
  
 `_O_CREAT`  
 建立並開啟新檔案以進行寫入。如果 *filename* 指定的檔案存在，則無作用。  
  
 `_O_EXCL`  
 如果 *filename* 指定的檔案存在，則傳回錯誤值。 僅適用於搭配 `_O_CREAT` 使用時。  
  
 `_O_RDONLY`  
 開啟檔案以僅供讀取。如果已指定此旗標，則無法指定 `_O_RDWR` 或 `_O_WRONLY`。  
  
 `_O_RDWR`  
 開啟檔案以進行讀取和寫入。如果已指定此旗標，則無法指定 `_O_RDONLY` 或 `_O_WRONLY`。  
  
 `_O_TRUNC`  
 開啟檔案並將現有檔案截斷為零長度。檔案必須具有寫入權限。 檔案的內容會遭到銷毀。 如果指定此旗標，則無法指定 `_O_RDONLY`。  
  
 `_O_WRONLY`  
 開啟檔案以僅供寫入。如果已指定此旗標，則無法指定 `_O_RDONLY` 或 `_O_RDWR`。  
  
## <a name="see-also"></a>請參閱  
 [_open、_wopen](../c-runtime-library/reference/open-wopen.md)   
 [_sopen、_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [全域常數](../c-runtime-library/global-constants.md)