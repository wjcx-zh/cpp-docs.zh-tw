---
title: XMMWORD
ms.date: 12/17/2019
f1_keywords:
- XMMWORD
helpviewer_keywords:
- XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
ms.openlocfilehash: 1116729883bf9b1b9342b30332bab5de6ba59015
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75319108"
---
# <a name="xmmword"></a>XMMWORD

用於具有 MMX 和 SSE （XMM）指令的128位多媒體運算元。

## <a name="syntax"></a>語法

> **XMMWORD**

## <a name="remarks"></a>備註

**XMMWORD**的目的是要代表與[__m128](../../cpp/m128.md)相同的類型。

## <a name="example"></a>範例

```asm
    movdqa   xmm0, xmmword ptr [ebx]
```

## <a name="see-also"></a>請參閱

[MASM BNF 文法](masm-bnf-grammar.md)
