---
title: ".SAFESEH |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .SAFESEH
dev_langs: C++
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bcbcafef4ad548ab784740a4130fc1679bf43f0a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="safeseh"></a>.SAFESEH
註冊函式做為結構化例外狀況處理常式。  
  
## <a name="syntax"></a>語法  
  
```  
  
.SAFESEH identifier  
```  
  
## <a name="remarks"></a>備註  
 *識別項*必須是本機定義的識別碼[PROC](../../assembler/masm/proc.md)或[EXTRN](../../assembler/masm/extrn.md)處理序 A[標籤](../../assembler/masm/label-masm.md)不允許。 。SAFESEH 指示詞需要[/safeseh](../../assembler/masm/ml-and-ml64-command-line-reference.md) ml.exe 命令列選項。  
  
 如需結構化例外狀況處理常式的詳細資訊，請參閱[/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)。  
  
 比方說，若要登錄的安全例外狀況處理常式，建立新的 MASM 檔案 （如下）、 與 /safeseh，組合，和將它新增到連結的物件。  
  
```  
.386  
.model  flat  
MyHandler   proto  
.safeseh    MyHandler  
end  
```  
  
## <a name="see-also"></a>另請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)