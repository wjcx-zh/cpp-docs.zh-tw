---
title: "暫存器使用方式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: ce58e2cf-afd3-4068-980e-28a209298265
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 705a8fef3043498c041ea7e5490a7b22c1db8e5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="register-usage"></a>暫存器使用方式
[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 架構提供 16 個一般目的的暫存器 (以下稱為整數暫存器)，以及 16 個可供浮點數使用的 XMM/YMM 暫存器。 動態暫存器是臨時暫存器，由呼叫者假設為跨呼叫終結。 需要靜態暫存器才能跨函式呼叫保留其值，且靜態暫存器必須由被呼叫者 (如果使用的話) 儲存。  
  
 下表描述如何跨函式呼叫使用每一個暫存器：  
  
||||  
|-|-|-|  
|登錄|狀態|用法|  
|RAX|動態|傳回值暫存器|  
|RCX|動態|第一個整數引數|  
|RDX|動態|第二個整數引數|  
|R8|動態|第三個整數引數|  
|R9|動態|第四個整數引數|  
|R10:R11|動態|必須由呼叫者視需要保留；在 syscall/sysret 指令中使用|  
|R12:R15|靜態|必須由被呼叫者保留|  
|RDI|靜態|必須由被呼叫者保留|  
|RSI|靜態|必須由被呼叫者保留|  
|RBX|靜態|必須由被呼叫者保留|  
|RBP|靜態|必須用作框架指標；必須由被呼叫者保留|  
|RSP|靜態|堆疊指標|  
|XMM0, YMM0|動態|第一個 FP 引數；使用 `__vectorcall` 時的第一個向量類型引數|  
|XMM1, YMM1|動態|第二個 FP 引數；使用 `__vectorcall` 時的第二個向量類型引數|  
|XMM2, YMM2|動態|第三個 FP 引數；使用 `__vectorcall` 時的第三個向量類型引數|  
|XMM3, YMM3|動態|第四個 FP 引數；使用 `__vectorcall` 時的第四個向量類型引數|  
|XMM4, YMM4|動態|必須由呼叫者視需要保留；使用 `__vectorcall` 時的第五個向量類型引數|  
|XMM5, YMM5|動態|必須由呼叫者視需要保留；使用 `__vectorcall` 時的第六個向量類型引數|  
|XMM6:XMM15, YMM6:YMM15|靜態 (XMM)、動態 (YMM 的上半部分)|必須由被呼叫端保留。 YMM 暫存器必須由被呼叫者視需要保留。|  
  
## <a name="see-also"></a>請參閱  
 [x64 軟體慣例](../build/x64-software-conventions.md)   
 [__vectorcall](../cpp/vectorcall.md)
