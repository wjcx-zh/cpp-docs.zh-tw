---
title: OPTION (MASM)
ms.date: 07/15/2020
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: 3d5bef52106b38487d1a2be248cff274f39e009c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830835"
---
# <a name="option"></a>OPTION

啟用及停用組合器的功能。

## <a name="syntax"></a>語法

> **`OPTION`***選項清單*

## <a name="remarks"></a>備註

可用的選項包括：

:::row:::
   :::column span="":::
      **`CASEMAP`**\
      **`DOTNAME`**\
      **`NODOTNAME`**\
      **`EMULATOR`**\
      **`NOEMULATOR`**\
      **`EPILOGUE`**\
      **`EXPR16`**
   :::column-end:::
   :::column span="":::
      **`EXPR32`**\
      **`LANGUAGE`**\
      **`LJMP`**\
      **`NOLJMP`**\
      **`M510`**\
      **`NOM510`**\
      **`NOKEYWORD`**
   :::column-end:::
   :::column span="":::
      **`NOSIGNEXTEND`**\
      **`OFFSET`**\
      **`OLDMACROS`**\
      **`NOOLDMACROS`**\
      **`OLDSTRUCTS`**\
      **`NOOLDSTRUCTS`**\
      **`PROC`**
   :::column-end:::
   :::column span="":::
      **`PROLOGUE`**\
      **`READONLY`**\
      **`NOREADONLY`**\
      **`SCOPED`**\
      **`NOSCOPED`**\
      **`SEGMENT`**\
      **`SETIF2`**
   :::column-end:::
:::row-end:::

LANGUAGE 的語法是 **`OPTION LANGUAGE:`** _`x`_ ，其中是、、、、 *`x`* 或其中之一 **`C`** **`SYSCALL`** **`STDCALL`** **`PASCAL`** **`FORTRAN`** **`BASIC`** 。 **`SYSCALL`****`PASCAL`** **`FORTRAN`** 不支援、、和 **`BASIC`** [`.MODEL`](dot-model.md) **`FLAT`** 。

## <a name="see-also"></a>另請參閱

[指示詞參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
