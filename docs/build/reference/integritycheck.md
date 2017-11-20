---
title: "-INTEGRITYCHECK |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /INTEGRITYCHECK
dev_langs: C++
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
ms.assetid: 2a293705-4396-421b-a5a5-693b4b867a85
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 20fa72f8cc2d12c719f0e50c250052a191b5ee81
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="integritycheck"></a>/INTEGRITYCHECK
指定必須檢查在載入時間的二進位檔映像的數位簽章。  
  
```  
  
/INTEGRITYCHECK[:NO]  
```  
  
## <a name="remarks"></a>備註  
 在頁首中的可執行檔的 DLL 檔案，這個選項會設定需要載入的映像中 Windows 記憶體管理員進行數位簽章檢查的旗標。 在 Windows Vista 之前的 Windows 版本會忽略此旗標。 適用於 64 位元 Dll 實作核心模式程式碼，而且建議所有的裝置驅動程式，必須設定這個選項。 如需詳細資訊，請參閱[核心模式程式碼簽署逐步解說](http://go.microsoft.com/fwlink/?linkid=237093)MSDN 網站上。  
  
## <a name="see-also"></a>另請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)