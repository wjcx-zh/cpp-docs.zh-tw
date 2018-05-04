---
title: -ALLOWBIND |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /allowbind
dev_langs:
- C++
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af4a9f3d898d0087f0e8e861ccfe72e4adadb1de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="allowbind"></a>/ALLOWBIND
指定 DLL 是否可以繫結。  
  
```  
  
/ALLOWBIND[:NO]  
```  
  
## <a name="remarks"></a>備註  
 **/ALLOWBIND**選項會設定位元 DLL 的標頭向 Bind.exe 表示繫結允許的映像中。 繫結可以允許更快載入時，載入器沒有重訂基底，並為每個參考的 DLL 執行位址的修復映像。 您可能不想要繫結，如果已經過數位簽署的 DLL — 繫結會使簽章。 如果在已使用位址空間配置隨機載入 (ASLR) 啟用映像，繫結會有任何作用 **/DYNAMICBASE**支援 ASLR 的 Windows 版本上。  
  
 使用 **/allowbind: no**防止 Bind.exe 繫結 DLL。  
  
 如需詳細資訊，請參閱[/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md)連結器選項。  
  
## <a name="see-also"></a>另請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)