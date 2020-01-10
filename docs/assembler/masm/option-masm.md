---
title: OPTION (MASM)
ms.date: 12/17/2019
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: bd50ac2e051db7f02ac077054e5856524745df54
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318744"
---
# <a name="option"></a>OPTION

啟用和停用組合器的功能。

## <a name="syntax"></a>語法

> **選項** *optionlist*

## <a name="remarks"></a>備註

可用的選項包括：

|||||
|-|-|-|-|
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**模擬器**|
|**NOEMULATOR**|**結尾**|**EXPR16**|**EXPR32**|
|**LANGUAGE**|**LJMP**|**NOLJMP**|**M510**|
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**投影**|
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|
|**PROC**|**說明**|**唯讀**|**NOREADONLY**|
|**範圍**|**NOSCOPED**|**SEGMENT**|**SETIF2**。|

LANGUAGE 的語法是**OPTION language：** <em>x</em>，其中*x*是 C、SYSCALL、STDCALL、PASCAL、FORTRAN 或 BASIC 其中之一。  不支援 SYSCALL、PASCAL、FORTRAN 和 BASIC [。模型](dot-model.md)平面。

## <a name="see-also"></a>請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
