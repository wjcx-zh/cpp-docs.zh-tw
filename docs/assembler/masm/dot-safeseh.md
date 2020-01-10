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
ms.openlocfilehash: 5953ad6bdf1d9d1b0070ce83dd1d764799b7440a
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317561"
---
# <a name="safeseh-32-bit-masm"></a>.SAFESEH （32-bit MASM）

將函數註冊為結構化例外狀況處理常式。 （僅限 32-bit MASM）。

## <a name="syntax"></a>語法

> **.SAFESEH** *識別碼*

## <a name="remarks"></a>備註

*識別碼*必須是本機定義的[進程](proc.md)或[EXTRN](extrn.md)程式的 ID。 不允許使用[標籤](label-masm.md)。 該.SAFESEH 指示詞需要[/safeseh](ml-and-ml64-command-line-reference.md) ml 命令列選項。

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

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
