---
title: "-DYNAMICBASE |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /dynamicbase
dev_langs: C++
helpviewer_keywords:
- -DYNAMICBASE editbin option
- DYNAMICBASE editbin option
- /DYNAMICBASE editbin option
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 07fd3c89cb2cff1fed06189ac66b2e67f7e52ade
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="dynamicbase"></a>/DYNAMICBASE
指定可執行映像是否可以使用位址空間配置隨機載入 (ASLR) 功能，於載入時隨機重訂基底。  
  
## <a name="syntax"></a>語法  
  
```  
  
/DYNAMICBASE[:NO]  
```  
  
## <a name="remarks"></a>備註  
 根據預設，連結器設定**/DYNAMICBASE**選項。  
  
 這個選項修改可執行映像的標頭，來表明載入器是否可以在載入時間為映像隨機重定基底。  
  
 Windows Vista、Windows Server 2008、Windows 7、Windows 8 和 Windows Server 2012 上可支援 ASLR。  
  
## <a name="see-also"></a>請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)   
 [Windows ISV 軟體安全性防禦措施](http://msdn.microsoft.com/library/bb430720.aspx)