---
title: "_get_FMA3_enable，_set_FMA3_enable |Microsoft 文件"
ms.custom: 
ms.date: 6/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _get_FMA3_enable
- _set_FMA3_enable
apilocation:
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
- math/_get_FMA3_enable
- math/_set_FMA3_enable
dev_langs: C++
helpviewer_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
ms.assetid: 4c1dc4bc-e86b-451b-9211-5a2ba6c98ee4
caps.latest.revision: "1"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b4c5a5a76a56567e0c0dd41a70b569327eda1cd4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="getfma3enable-setfma3enable"></a>_get_FMA3_enable _set_FMA3_enable
取得或設定旗標，指定是否將超越數學浮點數的程式庫函式使用 FMA3 指示在編譯程式碼適用於 X64 平台。  
  
## <a name="syntax"></a>語法  
  
```  
int _set_FMA3_enable(int flag);
int _get_FMA3_enable();
```  
  
### <a name="parameters"></a>參數
*旗標*  
設為 1 可啟用 FMA3 浮點數學的浮點程式庫函式的實作在 X64 平台，或為 0，以使用不會使用 FMA3 指令的實作。
  
## <a name="return-value"></a>傳回值  
如果啟用 FMA3 浮點數學的浮點程式庫函式的實作，則非零值。 否則為零。  
  
## <a name="remarks"></a>備註  
使用`_set_FMA3_enable`函式來啟用或停用的 CRT 程式庫中的浮點數學浮點函式中的 FMA3 指令的使用。 傳回值會反映在變更之後的使用中的實作。 如果 CPU 不支援 FMA3 指示，此函式無法在程式庫中啟用它們，並傳回值為零。 使用`_get_FMA3_enable`取得媒體櫃的目前狀態。 根據預設，在 X64 平台，CRT 啟始程式碼偵測到 CPU 支援 FMA3 指示，以及啟用或停用媒體櫃中的 FMA3 實作。
  
FMA3 實作使用不同的演算法，因為有些微差異計算的結果可能 observable FMA3 實作會啟用或停用，或電腦或是不支援 FMA3 之間。 如需詳細資訊，請參閱[浮點數的移轉問題](../../porting/floating-point-migration-issues.md)。

## <a name="requirements"></a>需求  
  
`_set_FMA3_enable`和`_get_FMA3_enable`函式只會在 X64 版本的 CRT。  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_set_FMA3_enable` <br /><br /> `_get_FMA3_enable`| C：\<math.h><br /><br /> C + +: \<h > 或\<math.h >|  
  
`_set_FMA3_enable` 和 `_get_FMA3_enable` 函式是 Microsoft 特有的。 如需相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
[浮點支援](../../c-runtime-library/floating-point-support.md)
[浮點數的移轉問題](../../porting/floating-point-migration-issues.md)  