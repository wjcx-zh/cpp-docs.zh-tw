---
title: .SAFESEH
ms.date: 11/05/2019
f1_keywords:
- .SAFESEH
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
ms.openlocfilehash: 4577bd5d76949dfb777a359c80d91814f1c45fe2
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703951"
---
# <a name="safeseh-32-bit-masm"></a>.SAFESEH （32-bit MASM）

將函數註冊為結構化例外狀況處理常式。 （僅限 32-bit MASM）。

## <a name="syntax"></a>語法

> .SAFESEH 識別碼

## <a name="remarks"></a>備註

*識別碼*必須是本機定義的[進程](../../assembler/masm/proc.md)或[EXTRN](../../assembler/masm/extrn.md)程式的 ID。 不允許使用[標籤](../../assembler/masm/label-masm.md)。 該.SAFESEH 指示詞需要[/safeseh](../../assembler/masm/ml-and-ml64-command-line-reference.md) ml 命令列選項。

如需結構化例外狀況處理常式的詳細資訊，請參閱[/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)。

例如，若要註冊安全的例外狀況處理常式，請建立新的 MASM 檔案（如下所示）、使用/safeseh 組合，然後將它加入至連結的物件。

```asm
.386
.model  flat
MyHandler   proto
.safeseh    MyHandler
end
```

## <a name="see-also"></a>請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>