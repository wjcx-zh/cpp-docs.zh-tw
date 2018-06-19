---
title: check_stack |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.check_stack
- check_stack_CPP
dev_langs:
- C++
helpviewer_keywords:
- check_stack pragma
- pragmas, check_stack
- pragmas, check_stack usage table
ms.assetid: f18e20cc-9abb-48b7-ad62-8d384875b996
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b393030961aa4695a16a9b50d49d0cae64cc4e0c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849765"
---
# <a name="checkstack"></a>check_stack
指示編譯器關閉堆疊探查，如果**關閉**(或**-**) 指定，或開啟堆疊探查，如果**上**(或**+**) 指定。  
  
## <a name="syntax"></a>語法  
  
```  
  
      #pragma check_stack([ {on | off}] )  
#pragma check_stack{+ | -}  
```  
  
## <a name="remarks"></a>備註  
 如果未指定引數，根據預設值處理堆疊探查。 這個 pragma 會在顯示該 pragma 後在定義的第一個函式生效。 堆疊探查不是巨集，也不是產生內嵌的函式。  
  
 如果您不指定的引數**check_stack** pragma，堆疊檢查會還原成在命令列上指定的行為。 如需詳細資訊，請參閱[編譯器參考](../build/reference/compiler-options.md)。 之間的互動 **#pragma check_stack**和[/Gs](../build/reference/gs-control-stack-checking-calls.md)下表摘要說明選項。  
  
### <a name="using-the-checkstack-pragma"></a>使用 check_stack pragma  
  
|語法|使用<br /><br /> /Gs 選項編譯？|動作|  
|------------|------------------------------------|------------|  
|**#pragma check_stack （)** 或<br /><br /> **#pragma check_stack**|[是]|關閉後續函式的堆疊檢查|  
|**#pragma check_stack （)** 或<br /><br /> **#pragma check_stack**|否|開啟後續函式的堆疊檢查|  
|**#pragma check_stack(on)**<br /><br /> 或 **#pragma check_stack +**|是或否|開啟後續函式的堆疊檢查|  
|**#pragma check_stack(off)**<br /><br /> 或 **#pragma check_stack-**|是或否|關閉後續函式的堆疊檢查|  
  
## <a name="see-also"></a>另請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)