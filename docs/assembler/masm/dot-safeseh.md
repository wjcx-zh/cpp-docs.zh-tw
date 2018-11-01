---
title: .SAFESEH
ms.date: 08/30/2018
f1_keywords:
- .SAFESEH
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
ms.openlocfilehash: adfb9106095de3d15bafb67172b001d0f4597418
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649848"
---
# <a name="safeseh"></a>.SAFESEH

註冊為結構化例外狀況處理常式的函式。

## <a name="syntax"></a>語法

> .SAFESEH 識別碼

## <a name="remarks"></a>備註

*識別項*必須是本機定義的識別碼[PROC](../../assembler/masm/proc.md)或是[EXTRN](../../assembler/masm/extrn.md)處理 A[標籤](../../assembler/masm/label-masm.md)不允許。 。SAFESEH 指示詞需要[/safeseh](../../assembler/masm/ml-and-ml64-command-line-reference.md) ml.exe 命令列選項。

如需有關結構化例外狀況處理常式的詳細資訊，請參閱 < [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)。

比方說，若要註冊的安全例外狀況處理常式，建立新的 MASM 檔案 （如下）、 /safeseh 與組合，和將它新增到連結的物件。

```asm
.386
.model  flat
MyHandler   proto
.safeseh    MyHandler
end
```

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>