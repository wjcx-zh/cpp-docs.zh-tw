---
title: -DYNAMICBASE |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /dynamicbase
dev_langs:
- C++
helpviewer_keywords:
- -DYNAMICBASE editbin option
- DYNAMICBASE editbin option
- /DYNAMICBASE editbin option
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d7a4cf7aa35d7ad6b41fc6d61f3f27662ae2c8d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="dynamicbase"></a>/DYNAMICBASE
指定可執行映像是否可以使用位址空間配置隨機載入 (ASLR) 功能，於載入時隨機重訂基底。  
  
## <a name="syntax"></a>語法  
  
```  
  
/DYNAMICBASE[:NO]  
```  
  
## <a name="remarks"></a>備註  
 根據預設，連結器設定 **/DYNAMICBASE**選項。  
  
 這個選項修改可執行映像的標頭，來表明載入器是否可以在載入時間為映像隨機重定基底。  
  
 Windows Vista、Windows Server 2008、Windows 7、Windows 8 和 Windows Server 2012 上可支援 ASLR。  
  
## <a name="see-also"></a>另請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)   
 [Windows ISV 軟體安全性防禦措施](http://msdn.microsoft.com/library/bb430720.aspx)