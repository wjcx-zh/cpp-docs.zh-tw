---
title: .SAFESEH | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .SAFESEH
dev_langs:
- C++
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ea34448b4dae0525e7feb2fd7cca310a95a6e3c
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052459"
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